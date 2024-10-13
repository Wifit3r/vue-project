<script>

export default {
  data() {
    return {
      isOpen:false,
      counter: 0,
      isHoverd: false,
      currentImage: 0,
      images: [
        '..\\src\\assets\\img\\IMG_4707.JPG',
        '..\\src\\assets\\img\\IMG_4679.JPG',
        '..\\src\\assets\\img\\IMG_4662.JPG',
        '..\\src\\assets\\img\\IMG_4627.JPG',
        '..\\src\\assets\\img\\IMG_4613.JPG',
        '..\\src\\assets\\img\\IMG_4599.JPG',
      ]
    };
  },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen;
    },
    nextImage() {
      this.currentImage =
        (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage =
        (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    setCurrentImage(index) {
      this.currentImage = index;
    } ,
    
  },
  computed:{
    isVisible() {
      if(this.counter%2  == 0){
        return this.isHoverd
      }
      else{
        setInterval(100)
      }
      this.counter ++;
      console.log(counter)
      return this.isHoverd
    }
  }
};
</script>

<template>
  <header>
    <div class="container1">
      <div class="header">
        <div class="header__inner">
          <div class="header__logo"><img
              src="./assets/img/logo.jpg"
              alt="">Фонд</div>
        </div>
          <nav class="nav">
            <nav v-if="isOpen" class="burger-menu">
              <div>
                <a class="nav_link" @mouseover="this.isHoverd = true"@mouseleave=" this.isHoverd = false" >Реквізити</a>
                  <div class="payment-border" v-show="isVisible" @mouseover="this.isHoverd = true" @mouseleave="this.isHoverd = false" >
                    <p class="dropdown-text" >Тут будуть платіжні реквізити</p>
                  </div>
              </div>
              <a class="nav_link" href="#gal">Діяльність</a>
              <a class="nav_link" href="">Новини</a>
              <a class="nav_link" id="meta" href="#card1">Мета</a>
            </nav>
            <button class="burger-btn" @click="toggleMenu">
             <span :class="{ 'open': isOpen }"></span>
             <span :class="{ 'open': isOpen }"></span>
             <span :class="{ 'open': isOpen }"></span>
            </button>
            <div class="container2">
              <div>
                <a class="nav_link" @mouseover="this.isHoverd = true"@mouseleave=" this.isHoverd = false" >Реквізити</a>
                  <div v-show="isVisible" @mouseover="this.isHoverd = true" @mouseleave="this.isHoverd = false" >
                    <p class="dropdown-text" >Тут будуть платіжні реквізити</p>
                  </div>
              </div>

              <a class="nav_link" href="#gal">Діяльність</a>
              <a class="nav_link" href="">Новини</a>
              <a class="nav_link" id="meta" href="#card1">Мета</a>
            </div>
          </nav>
      </div>
    </div>
  </header>
  
  <div class="card-container">
    <div class="card">
      <h3>Цілі Фонду</h3>
      <div class="spliter"></div>
      <p>Цілями благодійної діяльності Фонду є надання допомоги для сприяння законним інтересам бенефіціарів: особам,
        які постраждали чи можуть постраждати від збройної агресії, малозабезпеченим, тим хто у скрутному становищі,
        зокрема, за станом здоров’я та по іншим причинам. Крім того, Фонд активно сприяє соціальній реабілітації
        постраждалих, допомагаючи їм відновлювати психологічне та емоційне здоров’я через програми підтримки та
        реабілітаційні заходи. Одним з важливих напрямків діяльності є надання гуманітарної допомоги у вигляді
        продовольства, медикаментів, одягу та інших необхідних речей.</p>
    </div>
    <div class="card">
      <h3> Мета Фонду</h3>
      <div class="spliter"></div>
      <p>Фонд створено з метою:</p>
      <p>- здійснення благодійної діяльності в інтересах громадян, суспільства;</p>
      <p>- надання допомоги постраждалим від воєнних дій;</p>
      <p>- надання допомоги тим, хто у скрутному становищі за станом здоров’я та по іншим причинам;</p>
      <p>- надання допомоги дітям-сиротам, дітям з малозабезпечених та неблагополучних сімей, дітям з інвалідністю,
        внутрішньо переміщеним особам;</p>
      <p>- створення простору для самореалізації дітей та молоді;</p>
      <p>- пропаганди здорового способу життя;</p>
      <p>- фінансування проєктів із підтримки існуючих та створення і будівництва нових майданчиків, дитячих будинків та
        ін.;</p>
      <p>- затверджувати і виконувати благодійні програми.</p>
    </div>
    <div class="card-gal">
      <h3>Фото </h3>
      <div class="spliter"></div>
      <p>Приклади роботи фонду. Тут буде історія роботи фонду, або якась інша інформація</p>
    
    <div class="mainGallery">
    <div class="gallery" id="gal">
      <div class="main-image">
        <img :src="images[currentImage]" alt="Main Image" />
      </div>
      <div class="controls">
        <button @click="prevImage">◄</button>
        <button @click="nextImage">►</button>
      </div>
      <div class="thumbnails">
        <img v-for="(image, index) in images" :key="index" :src="image" @click="setCurrentImage(index)"
          :class="{ active: index === currentImage }" alt="Thumbnail" />
      </div>
    </div>
  </div>
</div>

  </div>
  
  <footer >
    <div class="contact-menu">
        <p>
          <i class="pi pi-inbox"></i>
          <a class="other-contacts" href="mailto:example@email.com">example@email.com</a>
        </p>
      </div>
      <div class="contact-menu">
        <p>
          <i class="pi pi-phone"></i>
          <a class="other-contacts" href="tel:+380123456789" >+38 (012) 345-67-89</a>
        </p>
    </div>
    <div class="contact-menu">
      <i class="pi pi-building"></i>
      <a class="map-point" href="https://www.google.com/maps/place/%D0%B2%D1%83%D0%BB.+%D0%97%D0%B0%D1%80%D1%96%D1%87%D0%BD%D0%B0,+%D0%9A%D1%83%D1%88%D0%BD%D0%B8%D1%86%D1%8F,+%D0%97%D0%B0%D0%BA%D0%B0%D1%80%D0%BF%D0%B0%D1%82%D1%81%D1%8C%D0%BA%D0%B0+%D0%BE%D0%B1%D0%BB%D0%B0%D1%81%D1%82%D1%8C,+90151/@48.4397938,23.2488711,13.82z/data=!4m10!1m2!2m1!1z0LLRg9C7LiDQl9Cw0YDRltGH0L3QsCwgMTM0LCDRgS4g0JrRg9GI0L3QuNGG0Y8sINCl0YPRgdGC0YHRjNC60LjQuSDRgC3QvSwg0JfQsNC60LDRgNC_0LDRgtGB0YzQutCwINC-0LHQuy4sINCj0LrRgNCw0ZfQvdCw!3m6!1s0x4739cf501076e815:0x3d161de6a7308553!8m2!3d48.4396973!4d23.2584358!15sCnvQstGD0LsuINCX0LDRgNGW0YfQvdCwLCAxMzQsINGBLiDQmtGD0YjQvdC40YbRjywg0KXRg9GB0YLRgdGM0LrQuNC5INGALdC9LCDQl9Cw0LrQsNGA0L_QsNGC0YHRjNC60LAg0L7QsdC7Liwg0KPQutGA0LDRl9C90LCSAQVyb3V0ZeABAA!16s%2Fg%2F11v5x88nd5?entry=ttu&g_ep=EgoyMDI0MDkxMS4wIKXMDSoASAFQAw%3D%3D">вул. Зарічна, 134, с. Кушниця,Хустський р-н, Закарпатська обл.,Україна</a>
    </div>
  </footer>
</template>

<style scoped>
.burger-btn {
  cursor: pointer;
  display: none; 
  flex-direction: column;
  justify-content: space-around;  
  width: 30px;
  height: 25px;
  background: transparent;
  border: none;
  padding: 0;
}
.payment-border{
  position: absolute;
  z-index: 1000;
  width: 50vw;
  margin-left: -45vw;
  margin-top: -5vh;  
}
.container2{
  display: flex;
  align-items: center;
  justify-content: space-between;
  justify-items: center;
  flex-direction: row;
}
@media (max-width: 768px) {
  .burger-btn {
    display: flex;
  }
  .container2{
    display: none;
  }
}

.burger-btn span {
  width: 100%;
  height: 3px;
  background: #333;
  transition: all 1s ease;
}

.burger-btn span.open:nth-child(1) {
  transform: rotate(45deg);
  position: relative;
  top: 8px;
}

.burger-btn span.open:nth-child(2) {
  opacity: 0;
}

.burger-btn span.open:nth-child(3) {
  transform: rotate(-45deg);
  position: relative;
  top: -8px;
}

.burger-menu {
  background-color: #333;
  padding: 20px;
  display: flex;  
  flex-direction: column; 
  position: absolute;
  margin-top: 36vh  ; 
  margin-left: -41vw;

}



.burger-menu ul {
  list-style: none;
  padding: 0;
}

.burger-menu li {
  margin: 15px 0;
}

.burger-menu a {
  color: #fff;
  text-decoration: none;
}
.spliter{
  background-color: wheat;  
  width: 100%;
  height: 1vh;
  border-radius: 1vw;
}
footer {
  background-color: rgb(229, 149, 91);
  flex: 0 0 auto;
  display: flex;
  align-items: center;
  align-content: center;
  height: 60px;
  width: 100vw;
  max-width: 100%;
  margin-top: 20px;
}



footer p{
  border-style: bold;
  border-width: 2px;
  width: 10vw;
}

footer i{
  margin-right: 1vw;
}

.mainGallery {
  margin-top: 20px;
}

.gallery {
  text-align: center;
}

.main-image img {
  width: 28vw;
  height: auto;
  max-width: 400px;
  border-radius: 10px;
}

.controls {
  margin-top: 20px;
  margin-bottom: 20px;
}

.controls button {
  margin-left: 5px;
  margin-right: 5px;
  width: 40px;
  height: 30px;
  border-radius: 5px;
  background-color: wheat;
  border: none;
}

.dropdown-text{
  background-color: wheat;
  font-size: 11px;
  display: flex;
  padding: 3vw;
  height: 100px;
  width: fit-content;
  justify-content: center;
  align-items: center;
  border-radius: 2vw;
  position:absolute;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.2);
}



.controls :hover {
  background-color: rgb(214, 144, 53);
  box-shadow: 2px;
}

.controls :active {
  background-color: burlywood;
  border-color: black;
}

;

.thumbnails {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.thumbnails img {
  width: 50px;
  height: 80px;
  margin: 0 3px;
  cursor: pointer;
  border: 4px solid transparent;
  transition: border-color 0.3s;
  border-color: burlywood;
  border-radius: 5px;
}

.thumbnails img.active {
  border-color: #333;
}

header {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

div {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

}

.name1 {
  margin-left: 10px;
}

.logomenu {
  background-color: rgb(232, 255, 187);
}

.menu1 {
  display: flex;
  align-items: center;
  justify-content: left;

}

.menu {
  margin-left: -10px;
  margin-top: -10px;
  background-color: burlywood;
  margin-left: 150px;

}

.logomenu {
  width: 15%;
  height: 15%;
  border-radius: 50%;
  max-width: 120px;
  max-height: 120px;
}

.header__inner {
  display: flex;
  justify-content: space-between;
  justify-items: center;
  inset-inline: center;

}


.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  justify-items: center;
  flex-direction: row;
  padding-top: 2vw;
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1;
  background-color: rgb(229, 149, 91);
  padding-bottom: 16px;
  max-height: 200px;
}

.header__logo {
  margin-left: 1vw;
  font-size: 50px;
  font-weight: 600;
  color: wheat;
  display: flex;
  align-items: center;
  font-size: 5vw;
}
.header__logo img {
  width: 100px;
  height: 100px;
  border-radius: 100px;
  margin-top: -18px;
  margin-right: 18px;
}
@media (max-width: 768px) {
  .header__logo {
  margin-top: 5vw;
  margin-left: -3vw;
  font-weight: 600;
  color: wheat;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 5vw;
}
.header__logo img{
  margin-left: 5vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
}
}
.nav {
  display: flex;
  align-items: center;
  align-content:center ;
  justify-items: center;
  font-size: 24 px;
  text-transform: uppercase;
  margin-right: 40px;
}

.nav_link {
  color: black;
  text-decoration: none;
  display: inline-block;
  vertical-align: top;
  margin: 10px;
  position: relative;
  padding: 10px;
  border-radius: 3px;
  border-width: 2px;  
  font-size: 24px;
  transition: transform 0.2s ease;
}

.nav_link::after {
  content: "";
  display: block;
  width: 100%;
  height: 3px;

  background-color: wheat;
  opacity: 0;
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1;
  transition: opacity 0.1s linear;
}


.nav_link:hover {
  color: wheat;
  transition:  color 0.2s linear;
  background-color: rgb(66, 60, 50);
  transition: background-color 0.6s linear;
  transform: translateY(5px) ;
}

.nav_link:hover::after {
  opacity: 1;
}

.contact-menu{
  border-radius: 8px;
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: space-around;
  margin-left: 10%;
  margin-right: 10%;
  height: 20px;
  width: 80%;
  font-size: 1vw;
  font-family: Arial, sans-serif;;
  margin: 2vw;
}

.contact-menu ul {
  list-style: none;
  display: flex;
  gap: 15px;

}
.contact-menu p {
display: flex;
flex-direction: row;
}
.contact-menu li {
  display: flex;
  align-items: center;

}

.contact-menu i.icon {
  font-size: 14px;
  margin-right: 5px;
}
.map-point {
  text-decoration: none;
  color: #000;
  font-weight: bold;
  text-wrap:wrap;
}
.other-contacts {
  text-decoration: none;
  color: #000;
  font-weight: bold;
  text-wrap:nowrap;
}

.contact-menu a:hover {
  text-decoration: underline;
}

.contact-menu li:last-child {
  font-weight: bold;
  color: #333;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.card-container {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 200px;
}


.card-gal {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 80%;
  max-width: 600px;
}
.card-gal h3{
  font-size:60px;
  padding-left: 2vw;
}

.card-gal h3 {
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #333;
}

.card-gal p {
  color: #666;
  line-height: 1.5;
}

.card-gal:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 600px;
  padding: 20px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 80%;
  max-width: 600px;
}

.card h3 {
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #333;  
  padding-left: 2vw;
}

.card p {
  color: #666;
  line-height: 1.5;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card-container {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 200px;
}

@media (max-width: 500px){
  .contact-menu{
    font-size: 7px;
  }
  
}

@media (max-width: 819px) {
  .contact-menu {
    font-size: 10px;
  }
}
</style>
