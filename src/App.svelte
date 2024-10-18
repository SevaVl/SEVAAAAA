
<!-- JS script -->
<script>
  import Comp1 from "./lib/Comp1.svelte";
  import Comp2 from "./lib/Comp2.svelte";
  import Comp3 from "./lib/Comp3.svelte";

  //Массив объектов, содержащий ссылки на 3 компонента
  const options = [
    { component: Comp1 },
    { component: Comp2 },
    { component: Comp3 },
  ];

  let selected = options[0]; //компонент по умолчанию
  let active_item = 0;


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
<!-- JS script -->


<!-- HTML -->
<main>
  <div class="holy-grail">
    <header>
      <nav>
        <h2>Тут много котят !</h2>
        
      </nav>
    </header>


    
    <div class="catscategories">
      
      <div>
        <button class = "button_cat"  on:click = {()=>onclick(0)}>
          Кот белый 
        </button>
      </div>

      <div>
        <button class = "button_cat" on:click = {()=>onclick(1)}>
          Кот чёрный
        </button>
      </div>

      <div>
        <button class = "button_cat" on:click = {()=>onclick(2)}>
          Кот красный
        </button>
      </div>

    </div>



    <div class="container">
      <div class="left-sidebar">
        <h2>Тут тоже много котят</h2>
        <p>Вот, смотрите</p>
        <div class="images_cats"><img src = "cat20.jpg" alt="{"котенок"}." width="200" /></div>
        <div class="images_cats"><img src = "cat30.jpg" alt="{"котенок"}." width="200" /></div>
        <div class="images_cats"><img src = "cat40.jpg" alt="{"котенок"}." width="200" /></div>
      </div>
      

      <div class="main-content">
        
        <!-- Динамические компоненты -->
        <svelte:component
          this={selected.component}
        />
        <h1>Смешные котята и пальма</h1>
        <div class="images_cats"><img src = "whitecatbaby.jpg" alt="{"котенок"}." width="500"/></div>
        <div class="images_cats"><img src = "181.jpg" alt="{"котенок"}." width="500"/></div>
        <div class="images_cats"><img src = "ittenVes170221.jpg" alt="{"котенок"}." width="500" height="" /></div>

      </div>


      <div class="right-sidebar">
        <h2>Интересный факт о котятах</h2>
        Они мяукают
        <div class="images_cats"><img src = "meow.jpg" alt="{"котенок"}." width="150" height="" /></div>
        <div class="images_cats"><img src = "котенок.jpg" alt="{"котенок"}." width="150" height="" /></div>
        <div class="images_cats"><img src = "cat10.jpg" alt="{"котенок"}." width="150" height="" /></div>
      </div>

    </div>



    <footer>
      <h2>На этом всё !</h2>
    </footer>
  </div>


</main>
<!-- HTML -->



<!-- CSS -->
<style>

  /* Global styles */
  :root {
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.5;
    font-weight: 400;
  }

  /* глобальный селектер (эти настройки будут применяться везде) */
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    }

    /* Грааль */
  .holy-grail {

    font-size: 15px;
    font-style: Georgia;
    font-family: sans-serif;
    color: #5537c7;

    display: flex;
    flex-direction: column;
    min-height: 100vh;
    /* background-image: url('vvvvv.jpg'); */
    background : #9c5fff ;
    border-radius: 8px;
  }

  /* Головняк */
  header {
    padding: em;
    text-align: center;
    border-radius: 8px;
  }

   /* Тут размещен весь контент*/
  .container {
    display: flex;
    flex-wrap: wrap;
    padding: 20px;
    flex: 1;
    text-align: center;
    border-radius: 8px;
    
  }
 /* Тут настройки фоток котов */
  .images_cats{
    border-radius: 12px;
  }


   /* Тут фон для расположения кнопок */
  .catscategories{
    display: flex;
    
    flex: 1;
    padding: 50px;
    /* width: 250px; */
    justify-content: space-around;
    border-radius: 8px;
  }

   /* Левый столбец */
  .left-sidebar {
    flex: 1;
    max-width: 250px;
    margin-right: 20px;
    background-color: #a957b4;
    padding: 20px;
    border-radius: 8px;
  }

   /* Середина, основной контент */
  .main-content {
    flex: 3;
    padding: 20px;
    background-repeat: no-repeat;
    background-size: cover;
    border-radius: 8px;
  }

 /* Правый столбец */
  .right-sidebar {
    flex: 1;
    max-width: 250px;
    margin-left: 20px;
    background-color: #a957b4;
    padding: 20px;
    border-radius: 8px;
  }

   /* Подвал */
  footer {
    background-color: #f37ab7;
    color: #5537c7;
    padding: 5em;
    text-align: center;
    height: 5px;
    margin-top: auto;
    border-radius: 8px;
  }
 /* кнопки */
  .button_cat {
    background-color: #b5e1f5; /* Green */
    border: none;
    color: rgb(77, 22, 43);
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    border-radius: 12px;

    font-size: 20px;
    font-style: Georgia;
    font-family: sans-serif;
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
</style>
<!-- CSS -->