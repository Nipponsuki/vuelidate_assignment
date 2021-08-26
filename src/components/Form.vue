<template>
  <div class="form-container">
    <h2 class="form-heading">Создание клиента</h2>
    <form class="form">
      <fieldset>
        <h3 class="section-heading">Личные данные</h3>
        <section>
          <label for="surname">
            Фамилия *
            <input
              type="text"
              id="surname"
              placeholder="Фамилия"
              aria-invalid="{}"
            />
            <ErrorMessage>Фамилия обязательно для заполения</ErrorMessage>
          </label>
          <label for="name">
            Имя *
            <input type="text" id="name" placeholder="Имя" />
            <ErrorMessage>Имя обязательно для заполения</ErrorMessage>
          </label>

          <label for="middlename">
            Отчество
            <input type="text" id="middlename" placeholder="Отчество" />
          </label>

          <label for="birthdate">
            Дата рождения *
            <input type="date" id="birthdate" />
            <ErrorMessage>Дата рождения обязательно для заполения</ErrorMessage>
          </label>

          <label for="phone">
            Номер телефона
            <input
              type="tel"
              id="phone"
              placeholder="+7__________"
              pattern="\+7\s?[\(]{0,1}9[0-9]{2}[\)]{0,1}\s?\d{3}[-]{0,1}\d{2}[-]{0,1}\d{2}"
            />
          </label>

          <label for="gender">
            Пол
            <select id="gender">
              <option value="female">Женский</option>
              <option value="male">Мужской</option>
            </select>
          </label>

          <label for="clients">
            Группа клиентов *
            <select id="clients" placeholder="Группа клиентов">
              <option value="vip">VIP</option>
              <option value="problem">Проблемные</option>
              <option value="oms">ОМС</option>
            </select>
            <ErrorMessage>Выберите группу клиентов</ErrorMessage>
          </label>
          <div class="checkbox">
            <input type="checkbox" id="sendSMS" />
            <label for="sendSMS">Не отправлять СМС</label>
          </div>
        </section>

        <h3 class="section-heading">Адрес</h3>
        <section>
          <label for="zip">
            Индекс
            <input type="number" id="zip" placeholder="Индекс" />
          </label>

          <label for="Country">
            Страна
            <input type="text" id="Country" placeholder="Страна" />
          </label>

          <label for="district">
            Область
            <input type="text" id="district" placeholder="Область" />
          </label>

          <label for="city">
            Город *
            <input type="text" id="city" placeholder="Город" />
          </label>

          <label for="street">
            Улица
            <input type="text" id="street" placeholder="Улица" />
          </label>

          <label for="house">
            Дом
            <input type="number" id="house" placeholder="Дом" />
          </label>
        </section>

        <h3 class="section-heading">Удостоверение личности</h3>
        <section>
          <label for="documentType">
            Тип документа
            <select id="documentType" placeholder="Тип документа">
              <option value="passport">Паспорт</option>
              <option value="birthdayDocument">Свидетельство о рождении</option>
              <option value="driving license">Вод. удостоверение</option>
            </select>
          </label>

          <label for="serial">
            Серия
            <input type="number" id="serial" placeholder="Серия" />
          </label>

          <label for="number">
            Номер
            <input type="number" id="number" placeholder="Номер" />
          </label>

          <label for="byWhom">
            Кем выдан
            <input type="text" id="byWhom" placeholder="Кем выдан" />
          </label>

          <label for="date">
            Дата выдачи *
            <input type="date" id="date" />
            <ErrorMessage>Дата рождения обязательно для заполения</ErrorMessage>
          </label>
        </section>
        <button type="submit">Создать</button>
        <Legend />
      </fieldset>
    </form>
  </div>
</template>

<script>
import Legend from "@/components/Legend.vue";
import ErrorMessage from "@/components/ErrorMessage.vue";

export default {
  components: {
    Legend,
    ErrorMessage,
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

  button {
    border: none;
    background: #5dbe88;
    border-radius: 4px;
    font-size: 1.6rem;
    color: #fff;
    padding: 1% 3%;
    cursor: pointer;
    transition: background 0.4s ease;
    margin: 2rem 0;
    width: 10rem;
    height: 3rem;

    &:hover {
      background: #3fb674;
    }

    &:disabled {
      background: #c5ccd7;
      pointer-events: none;
      cursor: not-allowed;
    }

    @media only screen and (max-width: 400px) {
      width: 100%;
      height: 3rem;
    }
  }
}
</style>
