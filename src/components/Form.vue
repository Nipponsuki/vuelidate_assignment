<template>
  <div class="form-container">
    <SuccessMessage v-if="isFormSubmitted" />
    <form class="form" @submit.prevent="onSubmit" v-else>
      <h2 class="form-heading">Создание клиента</h2>
      <fieldset :disabled="isFormSubmitting" ref="fieldset">
        <h3 class="section-heading">Личные данные</h3>
        <section>
          <label for="lastName">
            Фамилия *
            <input
              type="text"
              id="lastName"
              placeholder="Фамилия"
              :aria-invalid="errors && v$.form.lastName.$invalid"
              v-model="v$.form.lastName.$model"
            />
            <ErrorMessage v-if="errors && v$.form.lastName.$invalid">
              Фамилия обязательна для заполения
            </ErrorMessage>
          </label>
          <label for="firstName">
            Имя *
            <input
              type="text"
              id="firstName"
              placeholder="Имя"
              v-model="v$.form.firstName.$model"
              :aria-invalid="errors && v$.form.firstName.$invalid"
            />
            <ErrorMessage v-if="errors && v$.form.firstName.$invalid">
              Имя обязательно для заполения
            </ErrorMessage>
          </label>

          <label for="middleName">
            Отчество
            <input
              type="text"
              id="middleName"
              placeholder="Отчество"
              v-model="v$.form.middleName.$model"
            />
          </label>

          <label for="birthdate">
            Дата рождения *
            <input
              type="date"
              id="birthdate"
              v-model="form.birthdate"
              :aria-invalid="errors && v$.form.birthdate.$invalid"
            />
            <ErrorMessage v-if="errors && v$.form.birthdate.$invalid">
              Дата рождения обязательна для заполения
            </ErrorMessage>
          </label>

          <label for="phone">
            Номер телефона
            <input
              v-model="v$.form.phone.$model"
              type="tel"
              id="phone"
              placeholder="+7__________"
              :aria-invalid="form.phone !== '' && v$.form.phone.$invalid"
            />
            <ErrorMessage v-if="form.phone !== '' && v$.form.phone.$invalid">
              Введите правильный номер телефона
            </ErrorMessage>
          </label>

          <label for="gender">
            Пол
            <Multiselect
              id="gender"
              v-model="v$.form.gender.$model"
              :options="{ female: 'Женский', male: 'Мужской' }"
              class="multiselect-custom"
              placeholder="Выберите пол"
              :disabled="isFormSubmitting"
            ></Multiselect>
          </label>

          <label for="clients">
            Группа клиентов *
            <Multiselect
              :options="{ vip: 'VIP', problem: 'Проблемные', oms: 'ОМС' }"
              id="clients"
              v-model="v$.form.clients.$model"
              :aria-invalid="errors && v$.form.clients.$invalid"
              placeholder="Выберите группу клиентов"
              class="multiselect-custom multiselect-option-custom"
              :disabled="isFormSubmitting"
              noResultsText="Нет результатов"
              mode="tags"
              :createTag="true"
            ></Multiselect>

            <ErrorMessage v-if="errors && v$.form.clients.$invalid">
              Выберите группу клиентов
            </ErrorMessage>
          </label>

          <div class="checkbox">
            <input
              type="checkbox"
              id="sendSMS"
              v-model="v$.form.sendSMS.$model"
            />
            <label for="sendSMS">Не отправлять СМС</label>
          </div>
        </section>

        <h3 class="section-heading">Адрес</h3>
        <section>
          <label for="zip">
            Индекс
            <input
              type="number"
              id="zip"
              placeholder="Индекс"
              v-model="v$.form.zip.$model"
            />
          </label>

          <label for="country">
            Страна
            <input
              type="text"
              id="country"
              placeholder="Страна"
              v-model="v$.form.country.$model"
            />
          </label>

          <label for="district">
            Область
            <input
              type="text"
              id="district"
              placeholder="Область"
              v-model="v$.form.district.$model"
            />
          </label>

          <label for="city">
            Город *
            <input
              type="text"
              id="city"
              placeholder="Город"
              v-model="v$.form.city.$model"
              :aria-invalid="errors && v$.form.city.$invalid"
            />
            <ErrorMessage v-if="errors && v$.form.city.$invalid">
              Город обязателен для заполения
            </ErrorMessage>
          </label>

          <label for="street">
            Улица
            <input
              type="text"
              id="street"
              placeholder="Улица"
              v-model="v$.form.street.$model"
            />
          </label>

          <label for="house">
            Дом
            <input
              type="number"
              id="house"
              placeholder="Дом"
              v-model="v$.form.house.$model"
            />
          </label>
        </section>

        <h3 class="section-heading">Удостоверение личности</h3>
        <section>
          <label for="documentType">
            Тип документа
            <Multiselect
              id="documentType"
              v-model="v$.form.documentType.$model"
              class="multiselect-custom"
              :disabled="isFormSubmitting"
              :options="{
                passport: 'Паспорт',
                birthdayDoc: 'Свидетельство о рождении',
                driversLic: 'Вод. удостоверение',
              }"
              placeholder="Выберите тип документа"
            ></Multiselect>
          </label>

          <label for="serial">
            Серия
            <input
              type="number"
              id="serial"
              placeholder="Серия"
              v-model="v$.form.serial.$model"
            />
          </label>

          <label for="number">
            Номер
            <input
              type="number"
              id="number"
              placeholder="Номер"
              v-model="v$.form.number.$model"
            />
          </label>

          <label for="byWhom">
            Кем выдан
            <input
              type="text"
              id="byWhom"
              placeholder="Кем выдан"
              v-model="v$.form.byWhom.$model"
            />
          </label>

          <label for="date">
            Дата выдачи *
            <input
              type="date"
              id="date"
              v-model="v$.form.date.$model"
              :aria-invalid="errors && v$.form.date.$invalid"
            />
            <ErrorMessage v-if="errors && v$.form.date.$invalid">
              Дата рождения обязательно для заполения
            </ErrorMessage>
          </label>
        </section>
        <Button :type="'submit'" :disabled="isFormSubmitting">
          {{ isFormSubmitting ? "Создаeм..." : "Создать" }}
        </Button>
        <Legend />
      </fieldset>
    </form>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";
import Multiselect from "@vueform/multiselect";
import "@vueform/multiselect/themes/default.css";

import Legend from "@/components/Legend.vue";
import ErrorMessage from "@/components/ErrorMessage.vue";
import SuccessMessage from "./SuccessMessage.vue";
import Button from "./Button.vue";

import wait from "@/lib/wait.js";

export default {
  components: {
    Legend,
    ErrorMessage,
    SuccessMessage,
    Button,
    Multiselect,
  },

  setup() {
    return { v$: useVuelidate() };
  },
  data() {
    return {
      clientsOptions: ["VIP", "Проблемные", "OМС"],
      form: {
        firstName: "",
        lastname: "",
        middleName: "",
        birthdate: "",
        phone: "",
        gender: "female",
        clients: null,
        sendSMS: false,
        zip: "",
        country: "",
        district: "",
        city: "",
        street: "",
        house: "",
        documentType: "passport",
        serial: "",
        number: "",
        byWhom: "",
        date: "",
      },
      isFormSubmitting: false,
      isFormSubmitted: false,
      errors: false,
    };
  },
  validations() {
    return {
      form: {
        firstName: { required },
        lastName: { required },
        middleName: "",
        birthdate: { required },
        phone: {
          validatePhone(phone) {
            return /^$|^((\+7|7|8)+([0-9]){10})$/gm.test(phone);
          },
        },
        gender: "",
        clients: { required },
        sendSMS: false,
        zip: "",
        country: "",
        district: "",
        city: { required },
        street: "",
        house: "",
        documentType: "",
        serial: "",
        number: "",
        byWhom: "",
        date: { required },
      },
    };
  },

  methods: {
    async onSubmit() {
      this.errors = this.v$.form.$invalid;
      if (this.errors === false) {
        console.log(this.form);
        this.isFormSubmitting = true;
        await wait(3000);
        this.isFormSubmitted = true;
        this.isFormSubmitting = false;
        this.$nextTick(() => {
          this.v$.$reset();
        });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.form-container {
  border-radius: 4px;
  background: #fff;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 3rem 4rem;

  @media only screen and (max-width: 700px) {
    width: 100%;
    padding: 1rem 2rem;
  }

  .checkbox {
    justify-content: flex-start;
    display: flex;
    align-items: center;
    gap: 1rem;

    label {
      margin: 0;
    }

    @media only screen and (max-width: 700px) {
      margin: 1rem 0;
    }
  }

  .form-heading {
    font-size: 3.2rem;
  }

  .section-heading {
    font-size: 2.4rem;
    margin: 1rem 0;
  }

  section {
    display: grid;
    grid-template-columns: repeat(3, minmax(30rem, 1fr));
    gap: 1rem;

    @media only screen and (max-width: 1025px) {
      grid-template-columns: repeat(2, minmax(30rem, 1fr));
    }

    @media only screen and (max-width: 700px) {
      grid-template-columns: repeat(1, minmax(auto, 1fr));
      gap: 0;
    }
  }

  label {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    font-size: 1.4rem;
    gap: 1rem;
    position: relative;

    @media only screen and (max-width: 700px) {
      margin-bottom: 0.5rem;
    }
  }

  input:not([type="checkbox"]),
  select {
    font-size: 1.4rem;
    height: 4rem;
    width: 27rem;
    border-radius: 4px;
    border: 1px solid #d5d7db;
    padding-left: 1rem;
    margin-bottom: 1rem;

    &:focus {
      border-color: #25a1fb;
      outline: none;
    }
    &:disabled {
      background: #eceff3;
      pointer-events: none;
      cursor: not-allowed;
    }

    &.error {
      border-color: #f2123b;
    }

    @media only screen and (max-width: 700px) {
      width: 100%;
    }
  }

  .multiselect-custom {
    --ms-font-size: 1.4rem;
    --ms-border-color: #d5d7db;
    --ms-option-font-size: 1.4rem;
    --ms-bg-disabled: #eceff3;
    --ms-option-py: 0.7rem;

    height: 4.4rem;
    width: 28.2rem;
    margin: 0;
    margin-bottom: 1rem;

    &:focus {
      border-color: #25a1fb;
      outline: none;
      border-width: 1px;
      box-shadow: none;
    }

    @media only screen and (max-width: 700px) {
      width: 102.5%;
    }
  }
}
</style>
