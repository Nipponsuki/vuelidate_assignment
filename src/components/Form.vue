<template>
  <div class="form-container">
    <h2 form-heading>Добавление клиента</h2>
    <form class="form">
      <fieldset>
        <h3>Личные данные</h3>
        <section>
          <label for="name">
            Name
            <input type="text" id="name" placeholder="name" />
          </label>
          <label for="surname">
            Name
            <input type="text" id="surname" placeholder="surname" />
          </label>

          <label for="middle">
            middle
            <input type="text" id="middle" placeholder="middle" />
          </label>

          <label for="birthday">
            birthday
            <input type="date" id="birthday" placeholder="birthday" />
          </label>

          <label for="phone">
            phone
            <input
              type="tel"
              id="phone"
              placeholder="+7__________"
              pattern="\+7\s?[\(]{0,1}9[0-9]{2}[\)]{0,1}\s?\d{3}[-]{0,1}\d{2}[-]{0,1}\d{2}"
            />
          </label>
          <label for="gender">
            gender
            <select id="gender" placeholder="gender">
              <option value="male">Male</option>
              <option value="female">Female</option>
            </select>
          </label>

          <label for="gender">
            Clients
            <select id="Clients" placeholder="clients">
              <option value="vip">VIP</option>
              <option value="problem">Проблемные</option>
              <option value="oms">ОМС</option>
            </select>
          </label>

          <label for="send">
            send

            <input type="checkbox" id="send" />
          </label>
        </section>

        <h3>Адрес</h3>
        <section>
          <label for="zip">
            zip
            <input type="number" id="zip" placeholder="zip" />
          </label>

          <label for="Country">
            Name
            <input type="text" id="Country" placeholder="Country" />
          </label>

          <label for="dictrict">
            dictrict
            <input type="text" id="dictrict" placeholder="dictrict" />
          </label>

          <label for="city">
            city
            <input type="text" id="city" placeholder="city" />
          </label>

          <label for="street">
            street
            <input type="text" id="street" placeholder="street" />
          </label>

          <label for="house">
            house
            <input type="text" id="house" placeholder="house" />
          </label>
        </section>

        <h3>Паспорт</h3>
        <section>
          <label for="type">
            house
            <select id="type" placeholder="type">
              <option value="passport">Паспорт</option>
              <option value="birthday">Свидетельство о рождении</option>
              <option value="driving lisence">Вод. удостоверение</option>
            </select>
          </label>

          <label for="series">
            Series
            <input type="number" id="series" placeholder="series" />
          </label>

          <label for="number">
            number
            <input type="number" id="number" placeholder="number" />
          </label>

          <label for="byWhom">
            byWhom
            <input type="text" id="byWhom" placeholder="byWhom" />
          </label>

          <label for="date">
            date
            <input type="date" id="date" placeholder="date" />
          </label>
        </section>
        <button type="submit">submit</button>
      </fieldset>
    </form>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.form-container {
  border-radius: 4px;
  background: #fff;
  display: flex;
  flex-direction: column;
  padding: 4rem;

  h2 {
    font-size: 3.2rem;
  }

  h3 {
    font-size: 2.4rem;
  }

  section {
    display: grid;
    grid-template-columns: repeat(2, minmax(30rem, 1fr));
  }

  label {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    font-size: 1.4rem;
  }

  input {
    font-size: 1.4rem;
    height: 4rem;
    width: 27rem;
    border-radius: 4px;
  }
}
.form {
  margin: 0 auto;
}
</style>
