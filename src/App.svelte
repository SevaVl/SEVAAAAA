<script>
  import Comp1 from "./lib/Comp1.svelte";
  import Comp2 from "./lib/Comp2.svelte";
  import Comp3 from "./lib/Comp3.svelte";
  // import TopMenu from "./lib/TopMenu.svelte";

  // import DetectMessage from "./lib/Detector.svelte";

  //Массив объектов, содержащий ссылки на 3 компонента
  const options = [
    { component: Comp1 },
    { component: Comp2 },
    { component: Comp3 },
  ];

  let selected = options[0]; //компонент по умолчанию
  let active_item = 0;

  /**
   * @param {number} idcomp
   */
  function SelectComp(idcomp) {
    //Функция вызывается из верхнего меню и определяет
    //выбранный пользователем компонент
    selected = options[idcomp];
  }


  let clicked = false;

  function onclick(id){
    selected = options[id];

  }
</script>




<main>
  <div class="holy-grail">
    <header>
      <nav>
        <h2>Голова</h2>
        
      </nav>
    </header>


    
    <div class="catscategories">
      
      <h2>
        <button  on:click = {()=>onclick(0)}>Коты белые </button>
      </h2>
      <h2>
        <button  on:click = {()=>onclick(1)}>Коты чёрные</button>

        </h2>

      <h2>
        <button  on:click = {()=>onclick(2)}>Коты красные</button>
      </h2>

    </div>

    <div class="container">
      <div class="left-sidebar">
        <h2>А сюда никто не смотрит</h2>
        <p>Ну и ладно, не так уж и жалко</p>
      </div>

      <div class="main-content">
        <h1>Смешные котята и пальма</h1>
        <div class="item3"><img src = "whitecatbaby.jpg" alt="{"котенок"} котёнок." width="300" height="" /></div>
        <div class="item3"><img src = "181.jpg" alt="{"котенок"} котёнок." width="300" height="" />
        </div><div class="item3"><img src = "ittenVes170221.jpg" alt="{"котенок"} котёнок." width="300" height="" /></div>
        
        <!-- Динамические компоненты -->
        <svelte:component
          this={selected.component}
        />

      </div>
      <div class="right-sidebar">
        <h2>Белый котенок смотрит сюда</h2>
        <!-- <DetectMessage messagefrom={current_message} /> -->
         Ему очень интересно
      </div>
    </div>

    <footer>
      <h2>Подвал</h2>
    </footer>
  </div>
</main>

<style>
  /* Global styles */
  :root {
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.5;
    font-weight: 400;
  }

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  .holy-grail {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  header {
    
    background-color: #207ee9;
    color: #00144d;
    padding: em;
    text-align: center;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    padding: 20px;
    flex: 1;
    text-align: center;
    
  }

  .catscategories{
    display: flex;
    background-color: #cba6ec;
    flex: 1;
    padding: 50px;
    /* width: 250px; */
    justify-content: space-around;
  }

  .left-sidebar {
    flex: 1;
    max-width: 250px;
    margin-right: 20px;
    background-color: #83dd4e;
    padding: 20px;
  }

  .main-content {
    flex: 3;
    padding: 20px;
  }

  .right-sidebar {
    flex: 1;
    max-width: 250px;
    margin-left: 20px;
    background-color: #dbcb37;
    padding: 20px;
  }

  footer {
    background-color: #ca3636;
    color: #630000;
    padding: 5em;
    text-align: center;
    height: 5px;
    margin-top: auto;
  }

  /* Медиа-запросы - обеспечение респонсивности */
  @media (max-width: 1200px) {
    .left-sidebar,
    .right-sidebar {
      flex: 0 0 200px;
    }
  }

  @media (max-width: 992px) {
    .left-sidebar,
    .right-sidebar {
      flex: 0 0 150px;
    }
  }

  @media (max-width: 768px) {
    .container {
      flex-direction: column;
    }
    .left-sidebar,
    .right-sidebar {
      max-width: 100%;
      margin: 20px 0;
    }
    .main-content {
      flex: 1;
    }
  }

  /* Перенесен в TopMenu */
  /* @media (max-width: 480px) {
  header nav ul {
    flex-direction: column;
  }
  header nav li {
    margin-right: 0;
  }
} */
</style>
