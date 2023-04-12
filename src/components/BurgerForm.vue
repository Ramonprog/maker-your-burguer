<script>
export default {
  name: 'BurguerForm',

  data() { }
}
</script>

<template>
  <div>
    <p>componente de mensagem</p>

    <div class="form">
      <form>
        <div class="input-container">
          <label for="name">Nome do cliente: </label>
          <input type="text" id="name" placeholder="Digite seu nome" v-model="name" />
        </div>

        <div class="input-container">
          <label for="bread">Escolha o pão: </label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
          </select>
        </div>

        <div class="input-container">
          <label for="meat">Escolha a carne do seu Burger </label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>

        <div class="input-container">
          <label for="optional" id="optional-title">Selecione os opcionais: </label>
          <div class="checkbox">
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>
            <div class="checkbox-cointainer">
              <input type="checkbox" name="optional" id="optional" v-model="optional" value="salame" />
              <span>Salame</span>
            </div>

          </div>
        </div>

        <div class="input-container">
          <input type="submit" value="Criar meu Burger" class="submit-btn" />
        </div>
      </form>
    </div>
  </div>
</template>



<style scoped>
form {
  max-width: 400px;
  margin: 0 auto;
}

form .input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#optional {
  flex-direction: row;
  flex-wrap: wrap;
}

#optional-title {
  width: 100%;
}

.checkbox {
  width: 100%;
  display: flex;
  flex-wrap: wrap;

}

.checkbox-cointainer {
  display: flex;
  flex-wrap: wrap;
}

.checkbox-cointainer input {
  width: auto;
  margin-right: 10px;
  margin-bottom: 20px;
}

.checkbox-cointainer span {
  font-weight: bold;
  margin-right: 30px;
}

.submit-btn {
  margin-bottom: 100px;
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  transition: .5s;
}

.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>