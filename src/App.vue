<template>
  <div id="app">
    <main class="row">
      <div class="d-flex justify-content-center align-items-center">
        <div>
          <div class="d-flex justify-content-end">
            <div id="contagemDePontos">
              <span class="tituloPontos">PONTOS</span>
              <span class="valorPontos">{{pontos}}</span>
            </div>
          </div>
          <table class="tabela">
            <tbody>
              <tr>
                <td>
                  <div id="containerDicaRaca">
                    <div id="dicaRaca">
                      <span>
                      </span>
                    </div>
                  </div>
                </td>
                <th class="thHabilidades">Valor</th>
                <th class="thRaca">Raça</th>
                <th class="thBonus">Bonus</th>
                <th class="thTotal">TOTAL</th>
                <th class="thCusto">Custo</th>
              </tr>
              <tr>
              <th>
                <span class="thMaior">FOR</span>
                <span class="thMenor">Força</span>
              </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valfor" @change="validateValue('valfor', valfor)">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="racafor" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="bonusfor" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="text" class="campoTabela" disabled v-model="totalfor">
                </td>
                <td>
                  <input type="text" class="campoTabela custo" disabled v-model="custofor">
                </td>
              </tr>
              <tr>
                <th>
                  <span class="thMaior">DES</span>
                  <span class="thMenor">Destreza</span>
                </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valdes" @change="validateValue('valdes', valdes)">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="racades" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="bonusdes" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="text" class="campoTabela total" disabled v-model="totaldes">
                </td>
                <td>
                  <input type="text" class="campoTabela custo" disabled v-model="custodes">
                </td>
              </tr>
              <tr>
                <th>
                  <span class="thMaior">CON</span>
                  <span class="thMenor">Constituição</span>
                </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valcon" @change="validateValue('valcon', valcon)">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela"  v-model="racacon" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="bonuscon" @change="updateTotalCusto()">
                </td>
                <td>
                  <input type="text" class="campoTabela" disabled v-model="totalcon">
                </td>
                <td>
                  <input type="text" class="campoTabela custo" disabled v-model="custocon">
                </td>
              </tr>
              <tr>
                <th>
                  <span class="thMaior">INT</span>
                  <span class="thMenor">Inteligência</span>
                </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valint" @change="validateValue('valint', valint)">
                </td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="racaint" @change="updateTotalCusto()"></td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="bonusint" @change="updateTotalCusto()"></td>
                <td><input type="text" class="campoTabela total" disabled v-model="totalint" ></td>
                <td><input type="text" class="campoTabela custo" disabled v-model="custoint"></td>
              </tr>
              <tr>
                <th>
                  <span class="thMaior">SAB</span>
                  <span class="thMenor">Sabedoria</span>
                </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valsab" @change="validateValue('valsab', valsab)">
                </td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="racasab" @change="updateTotalCusto()"></td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="bonussab" @change="updateTotalCusto()"></td>
                <td><input type="text" class="campoTabela total" disabled v-model="totalsab"></td>
                <td><input type="text" class="campoTabela custo" disabled v-model="custosab"></td>
              </tr>
              <tr>
                <th>
                  <span class="thMaior">CAR</span>
                  <span class="thMenor">Carisma</span>
                </th>
                <td>
                  <input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model.number="valcar" @change="validateValue('valcar', valcar)">
                </td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="racacar" @change="updateTotalCusto()"></td>
                <td><input type="number" onkeydown="if(event.key==='.'){event.preventDefault();}" inputmode="numeric" class="campoTabela" v-model="bonuscar" @change="updateTotalCusto()"></td>
                <td><input type="text" class="campoTabela" disabled v-model="totalcar"></td>
                <td><input type="text" class="campoTabela custo" disabled v-model="custocar"></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </main>
    <footer id="sticky-footer" class="flex-shrink-0 py-4 bg-dark text-white-50">
      <div class="text-center py-2">
        <small>Desenvolvido por Lucas Correia (Discord: Noctus#3529) para a comunidade de jogadores de Tormenta20 do servidor do Discord <a href="https://discord.gg/8Kg8aWy" target="_blank">Área de RPG</a>.</small>
      </div>
      <div class="text-center py-2">
        <small>Tormenta20 é propriedade da <a href="https://jamboeditora.com.br" target="_blank">Jambo Editora</a>.</small>
      </div>
      <div class="text-center py-2">
        <small>Adaptado da <a href="https://trpg.orcnroll.com/habilidadeporpontos/" target="_blank">Compra de Habilidades por Pontos (TRPG)</a>, desenvolvido por Lucas Barreto.</small>
      </div>
    </footer>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  export default defineComponent({
    name: "App",
    data: () => {
      return{
        pontos: 10,
        valfor: 0,
        valdes: 0,
        valcon: 0,
        valint: 0,
        valsab: 0,
        valcar: 0,
        racafor: "",
        racades: "",
        racacon: "",
        racaint: "",
        racasab: "",
        racacar: "",
        bonusfor: "",
        bonusdes: "",
        bonuscon: "",
        bonusint: "",
        bonussab: "",
        bonuscar: "",
        totalfor: 0,
        totaldes: 0,
        totalcon: 0,
        totalint: 0,
        totalsab: 0,
        totalcar: 0,
        custofor: 0,
        custodes: 0,
        custocon: 0,
        custoint: 0,
        custosab: 0,
        custocar: 0,
      }
    },
    methods: {
      /** @returns {void} */
      validateValue(valname: String, value: number): void{
        if(value > 4){
          value = 4;
        }else if(value < -1){
          value = -1;
        }

        value = Math.floor(value);
        switch(valname){
          case 'valfor':
            this.valfor = value;
            break;
          case 'valdes':
            this.valdes = value;
            break;
          case 'valcon':
            this.valcon = value;
            break;
          case 'valint':
            this.valint = value;
            break;
          case 'valsab':
            this.valsab = value;
            break;
          case 'valcar':
            this.valcar = value;
            break;
        }
        this.updateTotalCusto()
      },
      /** @returns {void} */
      updateTotalCusto(): void{
        this.totalfor = this.valfor + parseInt(this.racafor ? this.racafor : "0") + parseInt(this.bonusfor ? this.bonusfor : "0");
        this.custofor = this.calcularCusto(this.valfor);

        this.totaldes = this.valdes + parseInt(this.racades ? this.racades : "0") + parseInt(this.bonusdes ? this.bonusdes : "0");
        this.custodes = this.calcularCusto(this.valdes);

        this.totalcon = this.valcon + parseInt(this.racacon ? this.racacon : "0") + parseInt(this.bonuscon ? this.bonuscon : "0");
        this.custocon = this.calcularCusto(this.valcon);

        this.totalint = this.valint + parseInt(this.racaint ? this.racaint : "0") + parseInt(this.bonusint ? this.bonusint : "0");
        this.custoint = this.calcularCusto(this.valint);

        this.totalsab = this.valsab + parseInt(this.racasab ? this.racasab : "0") + parseInt(this.bonussab ? this.bonussab : "0");
        this.custosab = this.calcularCusto(this.valsab);

        this.totalcar = this.valcar + parseInt(this.racacar ? this.racacar : "0") + parseInt(this.bonuscar ? this.bonuscar : "0");
        this.custocar = this.calcularCusto(this.valcar);

        this.pontos = 10 - this.custofor - this.custodes - this.custocon - this.custoint - this.custosab - this.custocar;
      },
      /** @returns {number} */
      calcularCusto(value: number): number{
        let custo: number = 0;
        switch(value){
          case -1:
            custo = -1;
            break;
          case 0:
            custo = 0;
            break;
          case 1:
            custo = 1;
            break;
          case 2:
            custo = 2
            break;
          case 3:
            custo = 4;
            break;
          case 4:
            custo = 7;
            break;
        }
        return custo;
      }
    }
  })
  </script>

<style scoped>
  #app{
    background-image: url('https://trpg.orcnroll.com/habilidadeporpontos/bg.jpg');
    background-attachment: fixed;
    background-position: top center;
    background-repeat: no-repeat;
    background-color: #d7c4a3;
    background-size: cover;
  }
  main{
    height: 80vh;
    min-height: 27rem;
    width: 100vw;
    min-width: 27rem;
  }
  footer{
    min-height: 20vh;
  }
  th{
    font-weight: 700;
    text-transform: uppercase;
    background-color: #2b2720;
    min-height: 2.5rem;
    width: 5rem;
    padding-top: 0.4rem;
    padding-bottom: 0.4rem;
    min-width: 4rem;
  }
  th span{
    display: block
  }
  .tabela{
    border-spacing: 0.4rem;
    border-collapse: separate;
    margin-top: 0.2rem;
    margin-right: 0;
    margin-left: 0;
    margin-bottom: 0;
  }
  table{
    border-collapse: collapse;
    border-spacing: 0;
    margin-top: 0;
    margin-right: 0;
    margin-left: 0;
    margin-bottom: 0;
  }
  .thMenor{
    font-size:0.5rem;
    line-height:0.5rem;
    color:#baa277
  }
  tr{
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    display: table-row;
  }
  td{
    display: table-cell;
    vertical-align: inherit;
    max-height: 2.5rem;
    max-width: 4rem;
    margin: 0;
    padding: 0;
  }
  th{
    font-weight: bold;
    text-transform: uppercase;
    color: #d1ba91;
    background-color: #2b2720;
    min-height: 2.5rem;
    width: auto;
    min-width: 4rem;
    padding-top: 0;
    padding-bottom: 0;
    text-align: center !important;
  }
  .thHabilidades{
    padding-top: 0.8rem;
    padding-bottom: 0.8rem;
    font-size: 0.8rem;
  }
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  input[type="number"]{
    -moz-appearance: textfield;
  }
  input{
    writing-mode: horizontal-tb !important;
    margin: 0;
    padding: 0;
  }
  .campoTabela{
    width: 4rem;
    height: 2.5rem;
    background-color: rgba(229, 210, 176, 0.4);
    box-sizing: border-box;
    color: #2b2720;
    border: 2px solid #2b2720;
    text-align: center;
    line-height: 2.4rem;
    font-size: 1rem;
    font-weight: bold;
  }
  #contagemDePontos{
    float:right;
    margin-right: 0.4rem;
    width: 4rem;
  }
  .tituloPontos{
    background-color: #6a0015 !important;
    display: block;
    box-sizing: border-box;
    text-align: center;
    color: #e5d2b0;
    line-height: 1.5rem;
    font-size: 0.8rem;
    height: 1.5rem;
    width: 4rem;
  }
  .valorPontos{
    display: block;
    box-sizing: border-box;
    height: 2.5rem;
    font-weight: bold;
    text-align: center;
    line-height: 2.3rem;
    font-size: 1.6rem;
    color: #6a0015;
    border: 2px solid #6a0015;
  }
  .thHabilidades, .thRaca, .thBonus, .thNivel, .thTotal, .thModificadores{
    padding-top: 0.8rem;
    padding-bottom: 0.8rem;
    font-size: 0.8rem;
  }
  .thTotal{
    background-color: #171511;
  }
  .thCusto{
    padding-top: 0.8rem;
    padding-bottom: 0.8rem;
    font-size: 0.8rem;
    color: #e5d2b0 !important;
    font-weight: 100;
    box-sizing: border-box;
    background-color: #6a0015 !important;
    font-weight: bold;
  }
  .custo{
    border-top: 0px solid transparent !important;
    border-right: 0px solid transparent !important;
    border-left: 0px solid transparent !important;
    border-bottom: 2px solid #6a0015;
    color: #6a0015;
    font-weight: 100 !important;
    box-sizing: border-box;
    background-color: transparent !important;
    height: 2.3rem;
    font-weight: bold;
  }


</style>

