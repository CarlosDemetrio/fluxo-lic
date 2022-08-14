<template>

  <div  class="flex" id="desktop" style="width: 100%">
    <div
      class="semestres flex no-wrap flex-center"
      :class="atual.nomeSemestre"
      v-for="atual in fluxo"
      :key="atual.semestre">

      <q-card style="height: 101px;margin-top: 10px;margin-bottom: 10px;margin-right: 10px"
              class="bg-grey text-center flex flex-center">
        <q-card-section style="height: 101px" class="bg-grey text-center flex flex-center"> {{ atual.semestre + '°' }}
        </q-card-section>
      </q-card>
      <div
        v-for="item in atual.materias"
        :key="item.nome" :class="item?.codigoSigaa"
        class="card-disciplina q-mx-lg"
      >
        <div style="width: 182px;height: 93px" v-if="item.tipo === 'espaco'"></div>
        <card-disciplina
          v-else-if="item.tipo !== 'espaco'"
          :ref="item.codigoSigaa"
          class="q-my-lg "
          :tipo="item?.tipo"
          :cadeiaSeletiva="item?.cadeiaSeletiva"
          :codigo-sigaa="item?.codigoSigaa"
          :sigla-departamento="item.siglaDepartamento"
          :creditos="item.creditos" :nome="item.nome"/>
      </div>
    </div>

    <div class="ponto-ligacao" id="ponto2-CIC0090-CIC0197"></div>

    <div class="ponto-ligacao" id="ponto-CIC0090-CIC0177"></div>
    <div class="ponto-ligacao" id="ponto2-CIC0090-CIC0177"></div>
    <div class="ponto-ligacao" id="ponto3-CIC0090-CIC0177"></div>
    <div class="line" id="line-CIC0090-CIC0197"></div>
    <div class="line" id="line-CIC0090-CIC0177"></div>
    <div class="line" id="line-CIC0090-CIC0097"></div>
    <div class="line" id="line-CIC0090-CIC0177-CIC0097"></div>
    <div class="line" id="line-TEF0011-MTC0012"></div>
    <div class="line" id="line1-CIC0005-CIC0207"></div>
    <div class="line" id="line2-CIC0005-CIC0207"></div>
    <div class="line" id="line3-CIC0005-CIC0207"></div>
    <div class="line" id="line4-CIC0005-CIC0207"></div>
    <div class="line" id="line1-MTC0012-CIC0210"></div>
    <div class="line" id="line2-MTC0012-CIC0210"></div>
    <div class="line" id="line1-MAT0025-MAT0026"></div>
    <div class="line" id="line2-MAT0025-MAT0026"></div>
    <div class="line" id="line3-MAT0025-MAT0026"></div>
    <div class="ponto-ligacao" id="ponto-MAT0025-MAT0026"></div>
    <div class="line" id="line1-CIC0206-CIC0224"></div>
    <div class="line" id="line2-CIC0206-CIC0224"></div>
    <div class="line" id="line3-CIC0206-CIC0224"></div>
    <div class="line" id="line3-1-CIC0206-CIC0224"></div>
    <div class="line" id="line4-CIC0206-CIC0224"></div>
    <div class="line" id="line4-1-CIC0206-CIC0224"></div>

    <div class="ponto-ligacao" id="ponto-MAT0025-CIC0189"></div>
    <div class="line" id="line1-MAT0025-CIC0189"></div>
    <div class="line" id="line2-MAT0025-CIC0189"></div>
    <div class="ponto-ligacao" id="ponto-CIC0214-CIC0215"></div>
    <div class="line" id="line-CIC0214-CIC0215"></div>
    <div class="line" id="line-CIC0097-CIC0101"></div>
    <div class="ponto-ligacao" id="ponto-CIC0093-CIC0105"></div>
    <div class="line" id="line1-CIC0093-CIC0105"></div>
    <div class="line" id="line2-CIC0093-CIC0105"></div>
    <div class="line" id="line3-CIC0093-CIC0105"></div>
    <div class="ponto-ligacao" id="ponto-CIC0093-CIC0189"></div>
    <div class="line" id="line-CIC0093-CIC0189"></div>
    <div class="ponto-ligacao" id="ponto-CIC0093-CIC0158"></div>
    <div class="line" id="line1-CIC0093-CIC0158"></div>
    <div class="line" id="line2-CIC0093-CIC0158"></div>
    <div class="line" id="line3-CIC0093-CIC0158"></div>
    <div class="line" id="line1-CIC0090-CIC0124"></div>
    <div class="line" id="line2-CIC0090-CIC0124"></div>

    <div class="line" id="line1-CIC0182-CIC0095"></div>
    <div class="line" id="line2-CIC0182-CIC0095"></div>
    <div class="line" id="line3-CIC0182-CIC0095"></div>
    <div class="line" id="line4-CIC0182-CIC0095"></div>

    <div class="line" id="line1-CIC0090-CIC0207"></div>
    <div class="line" id="line2-CIC0090-CIC0207"></div>
    <div class="line" id="line3-CIC0090-CIC0207"></div>
    <div class="line" id="line4-CIC0090-CIC0207"></div>
    <div class="line" id="line5-CIC0090-CIC0207"></div>
    <div class="line" id="line6-CIC0090-CIC0207"></div>



  </div>
  <div id="arrows"></div>
  <div v-if="requisitoDisciplinas.length > 0">
  </div>

</template>

<script>
import CardDisciplina from 'components/card-disciplina'
import {ref} from "vue"

export default {
  name: 'fluxoLic',
  components: {CardDisciplina},
  mounted() {
    this.gerarSetas()
    this.gerarLinhas()
  },
  data() {
    return {
      tab: ref('1'),
      splitterModel: ref(20),
      requisitoDisciplinas: ref([
        // segundo semestre
        {inicio: 'CIC0004', fim: 'CIC0090'},// ED
        // terceiro semestre
        {inicio: 'CIC0090', fim: 'CIC0182'},// logica
        {inicio: 'MAT0025', fim: 'EST0022'},// PE
        {inicio: 'CIC0090', fim: 'CIC0197'},// Tecnica prog
        // quarto semestre
        {inicio: 'CIC0090', fim: 'CIC0177'}, // APD
        {inicio: 'CIC0197', fim: 'CIC0093'}, // ling prog
        {inicio: 'MAT0025', fim: 'MAT0026'}, // c2
        // quinto
        {inicio: 'CIC0090', fim: 'CIC0097'}, // BD
        {inicio: 'CIC0093', fim: 'CIC0225'}, // sist operacionais
        {inicio: 'CIC0090', fim: 'CIC0207'}, // proj inter
        {inicio: 'CIC0005', fim: 'CIC0207'}, // proj inter
        {inicio: 'TEF0011', fim: 'MTC0012'}, // didatica fundamental
        // sexto
        {inicio: 'CIC0090', fim: 'CIC0124'}, // redes
        {inicio: 'CIC0197', fim: 'CIC0189'}, // proj analise algorit
        {inicio: 'MAT0025', fim: 'CIC0189'}, // proj analise algorit
        {inicio: 'MTC0012', fim: 'CIC0210/12'}, // prat pedag
        {inicio: 'CIC0207', fim: 'CIC0210/12'}, // prat pedag
        // setimo
        {inicio: 'CIC0197', fim: 'CIC0105'}, //eng software
        {inicio: 'CIC0097', fim: 'CIC0101'}, //sist informacao
        {inicio: 'CIC0124', fim: 'CIC0201'}, // seguranca
        {inicio: 'CIC0210/12', fim: 'CIC0211/13'}, //prat pedag 2
        {inicio: 'CIC0206', fim: 'CIC0224'}, // proj pesquisa lic
        // oitavo
        {inicio: 'CIC0093', fim: 'CIC0158'}, //informatica aplicada educ
        {inicio: 'CIC0211/13', fim: 'CIC0214/17'}, // estagio 1 \o/
        {inicio: 'CIC0224', fim: 'CIC0223'}, // prod cientifica
        {inicio: 'CIC0182', fim: 'CIC0095'}, // teoria da computacao
        //nono
        {inicio: 'CIC0214/17', fim: 'CIC0215/19'},
        {inicio: 'CIC0214/17', fim: 'CIC0216/21'},
      ]),
      fluxo: [
        {
          semestre: 1,
          nomeSemestre: 'primeiro',
          totalHoras: 210,
          totalCreditos: 14,
          materias: [
            {
              nome: 'espaco',
              tipo: 'espaco'
            },
            {
              nome: 'ALGORITMOS E PROG DE COMPUTADORES',
              codigoSigaa: 'CIC0004',
              creditos: '90h',
              siglaDepartamento: 'CIC',
              link: null,
            },

            {
              nome: 'ORGANIZAÇÃO DA EDUCAÇÃO BRASILEIRA',
              codigoSigaa: 'PAD0028',
              creditos: '60h',
              siglaDepartamento: 'PAD',
              link: null,
            },
            {
              nome: 'FORMAÇÃO DOCENTE EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0005',
              creditos: '60h',
              siglaDepartamento: 'LIC',
              link: null,
            }
          ]
        },
        {
          semestre: 2,
          nomeSemestre: 'segundo',
          totalHoras: 270,
          totalCreditos: 18,
          materias: [
            {
              nome: 'FUNDAMENTOS TEÓRICOS DA COMPUTAÇÃO',
              codigoSigaa: 'CIC0002',
              creditos: '60h',
              siglaDepartamento: 'CIC',
              link: null,
            },
            {
              nome: 'ESTRUTURA DE DADOS',
              codigoSigaa: 'CIC0090',
              creditos: '90h',
              siglaDepartamento: 'CIC',
              link: null,
            },
            {
              nome: 'CÁLCULO 1',
              codigoSigaa: 'MAT0025',
              creditos: '90h',
              siglaDepartamento: 'MAT',
              link: null,
            },
            {
              nome: 'espaco',
              tipo: 'espaco'
            },
            {
              nome: 'PSICOLOGIA DA EDUCAÇÃO',
              codigoSigaa: 'TEF0011',
              creditos: '60h',
              siglaDepartamento: 'TEF',
              link: null,
              tipo: 'OPT',
              cadeiaSeletiva: 7
            }
          ]
        },
        {
          semestre: 3,
          nomeSemestre: 'terceiro',
          totalHoras: 270,
          totalCreditos: 18,
          materias: [
            {
              nome: 'LÓGICA COMPUTACIONAL 1',
              codigoSigaa: 'CIC0182',
              creditos: '60h',
              siglaDepartamento: 'CIC',
              link: null,

            },
            {
              nome: 'TECNICAS DE PROGRAMAÇÃO 1',
              codigoSigaa: 'CIC0197',
              creditos: '60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'PROBABILIDADE E ESTATÍSTICA',
              codigoSigaa: 'EST0022',
              creditos: '60h',
              siglaDepartamento: 'EST',
              link: null
            },
            {
              nome: 'INTRODUCAO A ALGEBRA LINEAR',
              codigoSigaa: 'MAT0031',
              creditos: '60h',
              siglaDepartamento: 'EST',
              link: null
            }
          ]
        },
        {
          semestre: 4,
          nomeSemestre: 'quarto',
          totalHoras: 240,
          totalCreditos: 16,
          materias: [
            {
              nome: 'ARQUITETURA DE PROCESSADORES DIGITAIS',
              codigoSigaa: 'CIC0177',
              creditos: '60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'LINGUAGENS DE PROGRAMACAO',
              codigoSigaa: 'CIC0093',
              creditos: '60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'MÉTODOS DE PESQUISA NA LIC EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0206',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'CÁLCULO 2',
              codigoSigaa: 'MAT0026',
              creditos: '90h',
              siglaDepartamento: 'MAT',
              link: null
            }
          ]
        },
        {
          semestre: 5,
          nomeSemestre: 'quinto',
          totalHoras: 345,
          totalCreditos: 23,
          materias: [
            {
              nome: 'BANCOS DE DADOS',
              codigoSigaa: 'CIC0097',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'INTRODUÇÃO A SISTEMAS OPERACIONAIS',
              codigoSigaa: 'CIC0225',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null,
              tipo: 'OPT',
              cadeiaSeletiva: 5

            },
            {
              nome: 'PROD MATERIAL DIDÁTICO + SUPERV MATERIAL DIDÁTICO',
              codigoSigaa: 'CIC0208/09',
              creditos: ' 75h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'PROJ INTERDISCIPLINAR LIC EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0207',
              creditos: ' 60h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'DIDATICA FUNDAMENTAL',
              codigoSigaa: 'MTC0012',
              creditos: ' 60h',
              siglaDepartamento: 'TEF',
              link: null,
            }
          ]
        },
        {
          semestre: 6,
          nomeSemestre: 'sexto',
          totalHoras: 240,
          totalCreditos: 16,
          materias: [
            {
              nome: 'espaco',
              tipo: 'espaco'
            },
            {
              nome: 'REDES DE COMPUTADORES',
              codigoSigaa: 'CIC0124',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null,
              tipo: 'OPT',
              cadeiaSeletiva: 6
            },
            {
              nome: 'PROJETO E ANÁLISE DE ALGORITMOS',
              codigoSigaa: 'CIC0189',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },

            {
              nome: 'PRAT PED COMP 1 + SUPERV PRAT PED COMP 1',
              codigoSigaa: 'CIC0210/12',
              creditos: ' 90h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            }
          ]
        },
        {
          semestre: 7,
          nomeSemestre: 'setimo',
          totalHoras: 330,
          totalCreditos: 22,
          materias: [
            {
              nome: 'SISTEMAS DE INFORMACAO',
              codigoSigaa: 'CIC0101',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'SEGURANÇA COMPUTACIONAL',
              codigoSigaa: 'CIC0201',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'ENGENHARIA DE SOFTWARE',
              codigoSigaa: 'CIC0105',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'PRAT PED COMP 2 + SUPERV PRAT PED COMP 2',
              codigoSigaa: 'CIC0211/13',
              creditos: ' 90h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'PROJETO DE PESQUISA NA LICENCIATURA EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0224',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
          ]
        },
        {
          semestre: 8,
          nomeSemestre: 'oitavo',
          totalHoras: 405,
          totalCreditos: 22,
          materias: [

            {
              nome: 'TEORIA DA COMPUTACAO',
              codigoSigaa: 'CIC0095',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null,
              tipo: 'OPT',
              cadeiaSeletiva: 2
            },
            {
              nome: 'LÍNGUA DE SINAIS BRASILEIRA - BÁSICO',
              codigoSigaa: 'LIP0174',
              creditos: ' 60h',
              siglaDepartamento: 'LIP',
              link: null
            },
            {
              nome: 'INFORMATICA APLICADA A EDUCACAO',
              codigoSigaa: 'CIC0158',
              creditos: ' 60h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'ESTÁGIO SUP LC 1 + SUPR EST LIC 1',
              codigoSigaa: 'CIC0214/17',
              creditos: ' 105h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },

            {
              nome: 'PROD CIENTIFICA LIC EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0223',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'ADMIN DAS ORG EDUCATIVAS',
              codigoSigaa: 'PAD0038',
              creditos: ' 60h',
              siglaDepartamento: 'PAD',
              link: null,
              tipo: 'OPT',
              cadeiaSeletiva: 8
            },
          ]
        },
        {
          semestre: 9,
          nomeSemestre: 'nono',
          totalHoras: 330,
          totalCreditos: 22,
          materias: [
            {
              nome: 'TOPICOS AVANCADOS EM COMPUTADORES',
              codigoSigaa: 'CIC0087',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null,
              tipo: 'OPT',
            },
            {
              nome: 'espaco',
              tipo: 'espaco'
            },
            {
              nome: 'ESTÁGIO SUP LC 2 + SUPR ESTÁGIO LIC 2',
              codigoSigaa: 'CIC0215/19',
              creditos: '105h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'ESTÁGIO SUP LC 3 + SUPR ESTÁGIO LIC 3',
              codigoSigaa: 'CIC0216/21',
              creditos: ' 105h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },

          ]
        }
      ]
    }
  },
  methods: {
    // obtem cooordenadas do inicio ou fim
    obterCoordenadas(tipo) {
      const itens = this.requisitoDisciplinas.map(item => document.getElementsByClassName(tipo === 'fim' ? item.fim : item.inicio))
      const coordenadas = []

      for (let item of itens) {
        //pega elementos dentro de um DomCollection
        const coord = item[0].getBoundingClientRect()
        coordenadas.push(
          {
            left: coord.left + window.pageXOffset,
            top: coord.top + window.pageYOffset,
            width: coord.width || el.offsetWidth,
            height: coord.height || el.offsetHeight,
            x: coord.x,
            y: coord.y
          })
      }
      return coordenadas
    },
    gerarLinhas() {
      const coordenadasIniciais = this.obterCoordenadas('inicio')
      const coordenadasFinais = this.obterCoordenadas('fim')

      let html = ''
      for (const i in coordenadasIniciais) {
        if (coordenadasFinais[i].left === coordenadasIniciais[i].left &&
          coordenadasFinais[i].top !== 399 && coordenadasFinais[i].top) {
          const top = parseInt(coordenadasIniciais[i].top) + 117
          const left = parseInt(coordenadasIniciais[i].left) + 85
          const linha = '<div class="line linha-' + this.requisitoDisciplinas[i].inicio + '" style="position: absolute;top: ' + top + 'px;left: ' + left + 'px;height: 25px"></div>'
          html += linha
        }
      }
      const elem = document.querySelector("#arrows")
      elem.innerHTML += html
    },
    gerarSetas() {
      const coordenadasFinais = this.obterCoordenadas('fim')
      let html = ''
      for (const i in coordenadasFinais) {

        // se tiver 2 requisitos, as setas ficam uma do lado da outra
        const seRepetido = coordenadasFinais[i - 1]?.left === coordenadasFinais[i].left && coordenadasFinais[i - 1]?.top === coordenadasFinais[i].top ? 10 : 0
        const top = parseInt(coordenadasFinais[i].top)
        const left = parseInt(coordenadasFinais[i].left) + 85 + seRepetido
        const arrow = '<div class="arrow" style="top:' + top + 'px;left: ' + left + 'px; "><div class="line"></div><div class="point"></div></div>'
        html += arrow
      }
      const elem = document.querySelector("#arrows")
      elem.innerHTML += html
    }
  }
}
</script>

<style lang="scss">
.arrow {
  position: absolute;
  z-index: 10;
  height: 110px;
}

.line {
  width: 2px;
  margin-left: 4px;
  background: black;
  height: 15px;
}

.point {
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 10px solid black;
  float: right;
}

.ponto-ligacao {
  position: absolute;
  width: 0;
  height: 0;
  border: 3px solid black;
  border-radius: 50%;
}


// ED > TP

#CIC0090-CIC0197 > .line {
  height: 15px;
}

#line-CIC0090-CIC0197 {
  position: absolute;
  top: 280px;
  left: 164px;
  height: 2px;
  width: 230px;
}



#ponto2-CIC0090-CIC0197 {
  top: 278px;
  left: 396px;
}

// ED  > APD


#line-CIC0090-CIC0177 {
  position: absolute;
  top: 422px;
  left: 164px;
  height: 2px;
  width: 114px;
}

#line-CIC0090-CIC0097 {
  position: absolute;
  top: 562px;
  left: 164px;
  height: 2px;
  width: 114px;
}

#ponto-CIC0090-CIC0177 {
  top: 278px;
  left: 280px;
}

#ponto2-CIC0090-CIC0177 {
  top: 420px;
  left: 280px;
}
#ponto3-CIC0090-CIC0177 {
  top: 559px;
  left: 280px;
}

#line-CIC0090-CIC0177-CIC0097 {
  position: absolute;
  top: 280px;
  left: 278px;
  height: 284px
}

#ponto-CIC0090-CIC0097 {
  top: 278px;
  left: 280px;
}

// psic ed > didatica fundamental
#line-TEF0011-MTC0012 {
  position: absolute;
  top: 282px;
  left: 1084px;
  height: 283px;
}

// FDC > projeto lic
#line1-CIC0005-CIC0207 {
  position: absolute;
  top: 282px;
  left: 959px;
  height: 283px;
}

#line2-CIC0005-CIC0207 {
  position: absolute;
  top: 140px;
  left: 854px;
  height: 140px;
}

#line3-CIC0005-CIC0207 {
  position: absolute;
  top: 280px;
  left: 854px;
  height: 2px;
  width: 107px;
}

#line4-CIC0005-CIC0207 {
  position: absolute;
  top: 563px;
  left: 864px;
  height: 2px;
  width: 95px;
}

// didatica > prat pedag

#line1-MTC0012-CIC0210 {
  position: absolute;
  top: 682px;
  left: 1084px;
  height: 25px;
}

#line2-MTC0012-CIC0210 {
  position: absolute;
  top: 705px;
  left: 864px;
  height: 2px;
  width: 220px;
}


// c1 > c2
#ponto-MAT0025-MAT0026 {
  position: absolute;
  top: 278px;
  left: 626px;
}

#line1-MAT0025-MAT0026 {
  position: absolute;
  top: 422px;
  left: 750px;
  height: 2px;
  width: 106px;
}

#line2-MAT0025-MAT0026 {
  position: absolute;
  top: 280px;
  left: 750px;
  height: 143px;
}

#line3-MAT0025-MAT0026 {
  position: absolute;
  top: 280px;
  left: 624px;
  height: 2px;
  width: 127px;
}


// metodos de pesquisa > projeto pesquisa
#line1-CIC0206-CIC0224 {
  position: absolute;
  top: 540px;
  left: 630px;
  height: 25px;
}

#line2-CIC0206-CIC0224 {
  position: absolute;
  top: 563px;
  left: 630px;
  height: 2px;
  width: 95px;
}

#line3-CIC0206-CIC0224 {
  position: absolute;
  top: 563px;
  left: 725px;
  height: 136px;
}
#line3-1-CIC0206-CIC0224 {
  position: absolute;
  top: 710px;
  left: 725px;
  height: 138px;
}

#line4-CIC0206-CIC0224 {
  position: absolute;
  top: 846px;
  left: 725px;
  height: 2px;
  width: 125px;
}

#line4-1-CIC0206-CIC0224 {
  position: absolute;
  top: 846px;
  left: 860px;
  height: 2px;
  width: 226px;
}

// C1 > PROJETO E ANALISE ALGORIT
#ponto-MAT0025-CIC0189 {
  position: absolute;
  top: 420px;
  left: 752px;
}

#line1-MAT0025-CIC0189 {
  position: absolute;
  top: 420px;
  left: 750px;
  height: 283px;
}

#line2-MAT0025-CIC0189 {
  position: absolute;
  top: 703px;
  left: 634px;
  height: 2px;
  width: 118px;
}

// C1 > PE
#MAT0025-EST0022.arrow {
  top: 258px;
  left: 620px;
}

#MAT0025-EST0022 > .line {
  height: 38px;
}

// estagio 1 > estagio 2
#ponto-CIC0214-CIC0215 {
  position: absolute;
  top: 1126px;
  left: 856px;
}

#line-CIC0214-CIC0215 {
  position: absolute;
  top: 1128px;
  left: 624px;
  height: 2px;
  width: 232px;
}

// Bd > SI
#line-CIC0097-CIC0101 {
  position: absolute;
  top: 681px;
  left: 164px;
  height: 180px;
}

// tec program > eng softw
#ponto-CIC0093-CIC0105 {
  position: absolute;
  top: 421px;
  left: 396px;
}

#line1-CIC0093-CIC0105 {
  position: absolute;
  top: 423px;
  left: 394px;
  height: 2px;
  width: 127px;
}

#line2-CIC0093-CIC0105 {
  position: absolute;
  top: 423px;
  left: 520px;
  height: 424px;
}

#line3-CIC0093-CIC0105 {
  position: absolute;
  top: 845px;
  left: 520px;
  height: 2px;
  width: 105px;
}

#ponto-CIC0093-CIC0189 {
  position: absolute;
  top: 703px;
  left: 522px;
}

#line-CIC0093-CIC0189 {
  position: absolute;
  top: 705px;
  left: 520px;
  height: 2px;
  width: 105px;
}

// ling program > informatica aplicada a educacao
#ponto-CIC0093-CIC0158 {
  position: absolute;
  top: 562px;
  left: 396px;
}

#line1-CIC0093-CIC0158 {
  position: absolute;
  top: 564px;
  left: 394px;
  height: 2px;
  width: 108px;
}

#line2-CIC0093-CIC0158 {
  position: absolute;
  top: 564px;
  left: 500px;
  height: 424px;
}

#line3-CIC0093-CIC0158 {
  position: absolute;
  top: 987px;
  left: 500px;
  height: 2px;
  width: 125px;
}

// ED > REDES
#line1-CIC0090-CIC0124 {
  position: absolute;
  top: 563px;
  left: 278px;
  height: 143px;
}
#line2-CIC0090-CIC0124 {
  position: absolute;
  top: 705px;
  left: 278px;
  height: 2px;
  width: 117px;
}

// logica >> Teoria da comp
#line1-CIC0182-CIC0095 {
  position: absolute;
  top: 258px;
  left: 140px;
  height: 25px;
}
#line2-CIC0182-CIC0095 {
  position: absolute;
  top: 282px;
  left: 62px;
  height: 2px;
  width: 80px;
}

#line3-CIC0182-CIC0095 {
  position: absolute;
  top: 282px;
  left: 62px;
  height: 705px;
}
#line4-CIC0182-CIC0095 {
  position: absolute;
  top: 987px;
  left: 62px;
  height: 2px;
  width: 102px;
}

// ED >projeto lic

#line1-CIC0090-CIC0207 {
  position: absolute;
  top: 280px;
  left: 394px;
  height: 2px;
  width: 128px;
}
#line2-CIC0090-CIC0207 {
  position: absolute;
  top: 282px;
  left: 520px;
  height: 130px;
}
#line3-CIC0090-CIC0207 {
  position: absolute;
  top: 412px;
  left: 520px;
  height: 2px;
  width: 220px;
}
#line4-CIC0090-CIC0207 {
  position: absolute;
  top: 412px;
  left: 738px;
  height: 150px;
}
#line5-CIC0090-CIC0207 {
  position: absolute;
  top: 562px;
  left: 756px;
  height: 2px;
  width: 100px;
}
#line6-CIC0090-CIC0207 {
  position: absolute;
  top: 562px;
  left: 738px;
  height: 2px;
  width: 10px;
}




// bug de geracao que to com preguica de arrumar
.linha-CIC0182 {
  display: none;
}


</style>
