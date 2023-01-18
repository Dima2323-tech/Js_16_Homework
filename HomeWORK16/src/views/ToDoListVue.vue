<template>
  <div class="about">
    <div class="label">

      <h1 class="LabelProducts">To Do List</h1>

    </div>

    <div class="main">

      <div class="inputForm">

        <form class="formToDoList">
          <label class="LabelProducts">Products</label>
          <input v-model="Value" class="inputToDoValue" type="text">
        </form>

        <div class="btn">
          <button class="btnSubm" @click.self="takeToDoListValue" >Submit List Value</button>
        </div>

      </div>

      <div class="ListContainer">

        <h1 class="LabelProducts center">To Do List</h1>

        <div class="ListContent">

        </div>

        <h1 class="LabelProducts center">Completed Tasks</h1>

        <div class="ListCompContent">

        </div>
      </div>
    </div>

  </div>

</template>

<script>
export default {
  name: "ToDoListVue",
  data() {
    return {
      Value: ""

    }
  },
  methods: {
    takeToDoListValue() {
      let value = this.Value
      let content = document.querySelector('.ListContent')
      let globalContainer = document.createElement('div')
      let newElem = document.createElement("div")
      let dis = document.createElement('span')

      globalContainer.classList.add('Global')
      globalContainer.style.display = 'flex'
      dis.classList.add('Cross')
      newElem.classList.add('ListElem')
      dis.innerText = 'X'
      newElem.innerHTML = value;
      dis.style.marginLeft = 10 + 'px'
      dis.style.color = 'red'
      dis.style.fontWeight = 700

      content.appendChild(globalContainer)
      globalContainer.appendChild(newElem)
      globalContainer.appendChild(dis)


      for (let i = 0; i < newElem.length; i++) {
        newElem[i].onclick = function () {
          newElem.remove()
        }
      }
      this.deleteListValue()
      this.completedValue()

    },


    deleteListValue() {
      let cross = document.querySelectorAll('.Cross')
      for (let c = 0; c < cross.length; c++) {
        cross[c].onclick = function () {
          let div = this.parentElement;
          div.remove()
        }
      }
    },

    completedValue() {
      let content = document.querySelector('.ListCompContent')
      let elem = document.querySelectorAll('.ListElem')


      for (let i = 0; i < elem.length; i++) {
        elem[i].onclick = function () {
          let div = document.createElement('div')
          div.innerHTML = elem[i].textContent
          div.classList.add('Completed')
          div.style.textDecoration = 'line-through'
          content.appendChild(div)

          let divPare = this.parentElement
          divPare.remove()
        }
      }
    }
  }
}

</script>

<style scoped>
  .about{
    display: flex;
    align-items: center;
    max-height: 100vh;
    flex-flow: column;

  }
  .main{
    margin-top: 50px;
    display: flex;
  }

  label{
    text-align: center;
    font-size: 24px;
  }
  .formToDoList{
    display: flex;
    flex-flow: column;
  }
  .LabelProducts{
    text-decoration: none;
    color: hsla(160, 100%, 37%, 1);
    transition: 0.4s;
  }
  .btnSubm{
    margin-top: 20px;
    padding: 10px;
    border-radius: 10px;
    border: none;
    font-size: 14px;
    font-weight: 700;
    font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
    text-rendering: optimizeLegibility;
    background-color: hsla(160, 100%, 37%, 1);
    color: white;
    transition: 0.2s;
  }
  .btnSubm:hover{
    border-radius: 20px;
    padding: 15px;
    transition: 0.4s;
    background-color: rgb(184, 1, 0);
  }
  .inputToDoValue{
    margin-top: 20px;
    padding: 7px;
    border-radius: 10px;
    border: none;
    font-weight: 900;
    font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  }
  .ListContainer{
    width: 300px;
    margin-left: 35px;
    padding: 15px;
    background-color: white;
    color: black;
    border-radius:15px ;
  }
  .center{
    text-align: center;
  }
</style>