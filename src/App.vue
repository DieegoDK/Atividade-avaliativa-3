<template>
  <div id="app">
    <!-- START HEADER -->
    <header id="header" class="">
        <span class="logo fas fa-gamepad fa-7x" ><img src="#" alt="" /></span>
        <h1>Games Store: Unnamed</h1>
        <p>Jogos de qualidade e com preço que cabe no seu bolso</p>
    </header>
    <!-- END HEADER -->
    <div id="wrapper">
    <!-- START SLIDER -->
    <div class="slidder">
      <b-carousel
        id="carousel-fade"
        v-model="slide"
        :interval="4000"
        fade
        controls
        indicators
        
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <b-carousel-slide>
        <img
          slot="img"
          class="d-block img-fluid w-100"
          width="1024"
          height="480"
          src="//i.imgur.com/NI0Bo8B.jpg"
          alt="image slot"
        ></b-carousel-slide>

        <b-carousel-slide>
        <img
          slot="img"
          class="d-block img-fluid w-100"
          width="1024"
          height="480"
          src="//i.imgur.com/RXPLEbF.png"
          alt="image slot"
        ></b-carousel-slide>

        <b-carousel-slide>
        <img
          slot="img"
          class="d-block img-fluid w-100"
          width="1024"
          height="480"
          src="//i.imgur.com/aLxRUR4.jpg"
          alt="image slot"
        ></b-carousel-slide>

      </b-carousel>
    </div>
    <!-- END SLIDER -->
    <!-- START NAV BAR -->
    <div class="menu">
      <b-navbar toggleable="lg" type="light" variant="light">
        <b-navbar-brand href="#">
          <span class="fas fa-gamepad fa-1x"></span> GameStore: Unnamed
        </b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#">
              <span class="fas fa-home"></span> Home
            </b-nav-item>
            <b-nav-item href="#">
              <span class="fas fa-laptop"></span> PC
            </b-nav-item>
            <b-nav-item href="#">
              <span class="fab fa-playstation"></span> PS4
            </b-nav-item>
            <b-nav-item href="#">
              <span class="fab fa-xbox"></span> Xbox
            </b-nav-item>
            <b-nav-item href="pesquisa.pdf" target="_blank">
              <span class="fas fa-search"></span> Pesquisa
            </b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-navbar-nav>
              <b-nav-item href="#">
                <span class="fas fa-shopping-cart"></span>
                Carrinho
                <b-badge variant="secondary">{{carrinho}}</b-badge>
              </b-nav-item>
            </b-navbar-nav>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template slot="button-content">
                <i class="fas fa-user-circle"></i>
                <em>&nbsp;User</em>
              </template>
              <b-dropdown-item href="#">
                <i class="fas fa-user"></i> Profile
              </b-dropdown-item>
              <b-dropdown-item href="#">
                <i class="fas fa-sign-out-alt"></i> Sign Out
              </b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <!-- END NAV BAR -->
    <!-- START CONTENT -->
    <div>
      <b-card-group deck>
        <b-card title="" header-tag="header" footer-tag="footer">
          <h6 slot="header" class="mb-0">Produtos Populares</h6>
          <b-card-group deck>
             <b-card
              :title="produto[0]"
              :img-src="produtoImage0"
              img-alt="Image"
              img-top
            >
            <div v-for="variant0 in variants0" :key="variant0.variantId">
              <b-button block variant="outline-dark" size="sm" @mouseover="updateProduct0(variant0.variantImage0)">{{variant0.variantConsole}}</b-button>
            </div>
              <b-card-text>
                <span>{{descricao[0]}}</span></br>
                <span v-for="detalhe in detalhes">{{detalhe}} </br></span></br>
                <h6 style="color: green; text-align: center"><i class="fas fa-dollar-sign" style="color: green"></i> 100,00</h6>
                    <div style="text-align: center">
                    <h2 v-if="qtde > 10">Em Estoque</h2>
                    <h2 v-else-if="qtde <= 10 && qtde > 0">Ultimas Unidades</h2>
                    <h2 v-else>Fora de Estoque</h2>
                    </div>
              </b-card-text>
              <div slot="footer">
                <b-button block variant="outline-primary" @click="comprar" v-if="qtde >= 1">Comprar</b-button>
                <b-button block variant="outline-danger" v-else disabled class="disabledButton">Em falta</b-button>
              </div>
            </b-card>

           <b-card
              :title="produto[1]"
              :img-src="produtoImage1"
              img-alt="Image"
              img-top
            >
            <div v-for="variant1 in variants1" :key="variant1.variantId">
              <b-button block variant="outline-dark" size="sm" @mouseover="updateProduct1(variant1.variantImage1)">{{variant1.variantConsole}}</b-button>
            </div>
              <b-card-text>
                <span>{{descricao[1]}}</span></br>
                <span v-for="detalhe in detalhes">{{detalhe}} </br></span></br>
                <h6 style="color: green; text-align: center"><i class="fas fa-dollar-sign" style="color: green"></i> 100,00</h6>
                    <div style="text-align: center">
                    <h2 v-if="qtde > 10">Em Estoque</h2>
                    <h2 v-else-if="qtde <= 10 && qtde > 0">Ultimas Unidades</h2>
                    <h2 v-else>Fora de Estoque</h2>
                    </div>
              </b-card-text>
              <div slot="footer">
                <b-button block variant="outline-primary" @click="comprar" v-if="qtde >= 1">Comprar</b-button>
                <b-button block variant="outline-danger" v-else disabled class="disabledButton">Em falta</b-button>
              </div>
            </b-card>

           <b-card
              :title="produto[2]"
              :img-src="produtoImage2"
              img-alt="Image"
              img-top
            >
            <div v-for="variant2 in variants2" :key="variant2.variantId">
              <b-button block variant="outline-dark" size="sm" @mouseover="updateProduct2(variant2.variantImage2)">{{variant2.variantConsole}}</b-button>
            </div>
              <b-card-text>
                <span>{{descricao[2]}}</span></br>
                <span v-for="detalhe in detalhes">{{detalhe}} </br></span></br>
                <h6 style="color: green; text-align: center"><i class="fas fa-dollar-sign" style="color: green"></i> 100,00</h6>
                    <div style="text-align: center">
                    <h2 v-if="qtde > 10">Em Estoque</h2>
                    <h2 v-else-if="qtde <= 10 && qtde > 0">Ultimas Unidades</h2>
                    <h2 v-else>Fora de Estoque</h2>
                    </div>
              </b-card-text>
              <div slot="footer">
                <b-button block variant="outline-primary" @click="comprar" v-if="qtde >= 1">Comprar</b-button>
                <b-button block variant="outline-danger" v-else disabled class="disabledButton">Em falta</b-button>
              </div>
            </b-card>
          </b-card-group>
        </b-card>
      </b-card-group>
      <footer id="footer">
            <section>
                <h2>Aliquam sed mauris</h2>
                <p>Sed lorem ipsum dolor sit amet et nullam consequat feugiat consequat magna adipiscing tempus etiam
                    dolore veroeros. eget dapibus mauris. Cras aliquet, nisl ut viverra sollicitudin, ligula erat
                    egestas velit, vitae tincidunt odio.</p>
                <ul class="actions">
                    <li><b-button variant="outline-light" size="sm">Learn More</b-button></li>
                </ul>
            </section>
            <section>
                <h2>Etiam feugiat</h2>
                <dl class="alt">
                    <dt>Address</dt>
                    <dd>1234 Somewhere Road &bull; Nashville, TN 00000 &bull; USA</dd>
                    <dt>Phone</dt>
                    <dd>(000) 000-0000 x 0000</dd>
                    <dt>Email</dt>
                    <dd><a href="#">information@unnamed.com.br</a></dd>
                </dl>
                <ul class="icons">
                    <li><a href="#" class="icon fa-twitter alt"><span class="label">Twitter</span></a></li>
                    <li><a href="#" class="icon fa-facebook alt"><span class="label">Facebook</span></a></li>
                    <li><a href="#" class="icon fa-instagram alt"><span class="label">Instagram</span></a></li>
                    <li><a href="#" class="icon fa-github alt"><span class="label">GitHub</span></a></li>
                    <li><a href="#" class="icon fa-dribbble alt"><span class="label">Dribbble</span></a></li>
                </ul>
            </section>
            <p class="copyright">&copy; Untitled. Design: Diego Gabriel Kachuba.</p>
        </footer>
      </div>
    </div>
    <!-- END CONTENT -->
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  data() {
    return {
      slide: 0,
      sliding: null,
      carrinho: 0,
      produto: ["Grand theft Auto V", "Fifa 19", "Need For Speed: Payback"],
      produtoImage0: "//i.imgur.com/KJ9wgar.jpg",
      produtoImage1: "//i.imgur.com/MQKn6xn.jpg",
      produtoImage2: "//i.imgur.com/q79BOu5.jpg",
      descricao: ["Estudio: Rockstar Games", "Estudio: Electronic Arts, EA Sports", "Estudio: Electronic Arts, Ghost Games"],
      detalhes: [
        "Requisitos PC:",
        " Processador: Intel Core i5 3470 @ 3.2GHZ (4 CPUs) / AMD X8 FX-8350 4GHZ (8 CPUs)",
        " Memória: 8GB.",
        " Placa de Vídeo: NVIDIA GTX 660 2GB / AMD HD7870 2GB.",
        " Espaço no HD: 65GB."
      ],
      qtde: 11,
      variants0: [
        {
          variantId: 1,
          variantConsole: "PS4",
          variantImage0: "//i.imgur.com/KJ9wgar.jpg"
        },
        {
          variantId: 2,
          variantConsole: "Xbox One",
          variantImage0: "//i.imgur.com/zCmN9i6.png"
        },
        {
          variantId: 3,
          variantConsole: "PC",
          variantImage0: "//i.imgur.com/Rz5sbypg.jpg"
        }
      ],
      variants1: [
        {
          variantId: 1,
          variantConsole: "PS4",
          variantImage1: "//i.imgur.com/MQKn6xn.jpg"
        },
        {
          variantId: 2,
          variantConsole: "Xbox One",
          variantImage1: "//i.imgur.com/MlEbj8C.jpg"
        },
        {
          variantId: 3,
          variantConsole: "PC",
          variantImage1: "//i.imgur.com/DwiiHiq.jpg"
        }
      ],
      variants2: [
        {
          variantId: 1,
          variantConsole: "PS4",
          variantImage2: "//i.imgur.com/q79BOu5.jpg"
        },
        {
          variantId: 2,
          variantConsole: "Xbox One",
          variantImage2: "//i.imgur.com/FvfREpv.jpg"
        },
        {
          variantId: 3,
          variantConsole: "PC",
          variantImage2: "//i.imgur.com/eSyJZu7.png"
        }
      ],
    };
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    },
    updateProduct0(variantImage0) {
      this.produtoImage0 = variantImage0;
    },
    updateProduct1(variantImage1) {
      this.produtoImage1 = variantImage1;
    },
    updateProduct2(variantImage2) {
      this.produtoImage2 = variantImage2;
    },
    comprar: function() {
      this.carrinho += 1;
      this.qtde -= 1;
    }
  }
};
</script>

<style>
@import url("https://use.fontawesome.com/releases/v5.8.1/css/all.css");
@import url("./assets/css/main.css");
.card-title{
  text-align: center;
}
.card-img-top{
  text-align: center !important;
  margin: 0 auto;
}
.navbar{
  border-radius: 4px !important;
  margin-top: 10px;
  margin-bottom: 10px;
}
.carousel-inner{
  border-radius: 4px !important;
}

#header h1,#header span,#header p, #footer, #footer a{
  color: #ffff;
}


</style>
