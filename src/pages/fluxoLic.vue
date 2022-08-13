<template>

<!--  HTML gerado para desktop-->
  <div v-if="$q.platform.is.desktop" class="flex no-wrap scroll-x q-mt-lg" id="desktop" style="width: 100%">
    <div class="flex-column q-mx-lg" style="margin: 30px" :class="atual.nomeSemestre" v-for="atual in fluxo" :key="atual.semestre">
      <q-card>
        <q-card-section class="bg-grey-4 text-center">
          <div>
            {{ atual.semestre + '° '}} semestre
          </div>
        </q-card-section>
      </q-card>
      <q-card class="q-mt-sm">
        <q-card-section class="bg-grey q-mx-none text-weight-bold text-center">
          <span >Créditos: {{atual.totalCreditos}} | CH: {{atual.totalHoras}}h</span>
        </q-card-section>
      </q-card>
      <div v-for="item in atual.materias"
           :key="item.nome" :class="item?.codigoSigaa"
            class="card-disciplina"
      >
        <div style="width: 224px;height: 152px" v-if="item.tipo === 'espaco'"></div>
        <card-disciplina
          v-else-if="item.tipo !== 'espaco'"
          :ref="item.codigoSigaa"
          class="q-my-lg "
          :tipo="item?.tipo"
          :cadeiaSeletiva="item?.cadeiaSeletiva"
          :codigo-sigaa="item?.codigoSigaa"
          :sigla-departamento="item.siglaDepartamento"
          :creditos="item.creditos" :nome="item.nome" />
      </div>
    </div>
    <div class="arrow" :id="linha.inicio + '-' + linha.fim" v-for="linha in requisitoDisciplinas" :key="linha.inicio+linha.fim">
      <div class="line"></div>
      <div class="point"></div>
    </div>
  </div>

<!--  HTML GERADO PARA MOBILE-->
  <div v-if="$q.platform.is.mobile">
  </div>
  <div v-if="requisitoDisciplinas.length > 0">
  </div>

</template>

<script>
import CardDisciplina from 'components/card-disciplina'
import {ref} from "vue"
export default {
  name: 'fluxoLic',
  components: { CardDisciplina },
  mounted() {
    this.gerarLinhas()
    mermaid.initialize()
  },
  data () {
    return {
      tab: ref('1'),
      splitterModel: ref(20),
      requisitoDisciplinas: ref([]),
      fluxo: [
        {
          semestre: 1,
          nomeSemestre: 'primeiro',
          totalHoras: 210,
          totalCreditos: 14,
          materias: [
            {
              nome: 'ALGORITMOS E PROGRAMAÇÃO DE COMPUTADORES',
              codigoSigaa: 'CIC0004',
              creditos: '4-2 | 90h',
              siglaDepartamento: 'CIC',
              link: null,
            },
            {
              nome: 'espaco',
              tipo: 'espaco'
            },
            {
              nome: 'ORGANIZAÇÃO DA EDUCAÇÃO BRASILEIRA',
              codigoSigaa: 'PAD0028',
              creditos: '2-2 | 60h',
              siglaDepartamento: 'PAD',
              link: null,
            },
            {
              nome: 'FORMAÇÃO DOCENTE EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0005',
              creditos: '3-1 | 60h',
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
              nome: 'ESTRUTURA DE DADOS',
              codigoSigaa: 'CIC0090',
              creditos: '4-2 | 90h',
              siglaDepartamento: 'CIC',
              link: null,
            },
            {
              nome: 'FUNDAMENTOS TEÓRICOS DA COMPUTAÇÃO',
              codigoSigaa: 'CIC0002',
              creditos: '2-2 | 60h',
              siglaDepartamento: 'CIC',
              link: null,
            },
            {
              nome: 'CÁLCULO 1',
              codigoSigaa: 'MAT0025',
              creditos: '2-2 | 60h',
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
              creditos: '2-2 | 60h',
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
              creditos: '2-2 60h',
              siglaDepartamento: 'CIC',
              link: null,

            },
            {
              nome: 'PROBABILIDADE E ESTATÍSTICA',
              codigoSigaa: 'EST0022',
              creditos: '2-2 60h',
              siglaDepartamento: 'EST',
              link: null
            },
            {
              nome: 'TECNICAS DE PROGRAMAÇÃO 1',
              codigoSigaa: 'CIC0197',
              creditos: '2-2 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'INTRODUCAO A ALGEBRA LINEAR',
              codigoSigaa: 'MAT0031',
              creditos: '4-0 60h',
              siglaDepartamento: 'EST',
              link: null
            }
          ]
        },
        {
          semestre: 4,
          nomeSemestre: 'quarto',
          totalHoras: 300,
          totalCreditos: 20,
          materias: [
            {
              nome: 'ORGANIZAÇÃO DE ARQUIVOS',
              codigoSigaa: 'CIC0092',
              creditos: '2-2 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'LINGUAGENS DE PROGRAMACAO',
              codigoSigaa: 'CIC0093',
              creditos: '4-0 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'ARQUITETURA DE PROCESSADORES DIGITAIS',
              codigoSigaa: 'CIC0177',
              creditos: '4-0 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'MÉTODOS DE PESQUISA NA LICENCIATURA EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0206',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'CÁLCULO 2',
              codigoSigaa: 'MAT0026',
              creditos: '4-2 90h',
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
              nome: 'PROJETO INTERDISCIPLINAR DE LICENCIATURA EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0207',
              creditos: ' 60h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'PRODUÇÃO DE MATERIAL DIDÁTICO',
              codigoSigaa: 'CIC0208',
              creditos: ' 75h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'SUPERVISÃO DE PRODUÇÃO DE MATERIAL DIDÁTICO',
              codigoSigaa: 'CIC0209',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
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
              nome: 'PROJETO E ANÁLISE DE ALGORITMOS',
              codigoSigaa: 'CIC0189',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null
            },
            {
              nome: 'PRAT PED COMP 2 + SUPERV PRAT PED COMP 2',
              codigoSigaa: 'CIC0210/12',
              creditos: ' 90h + 30h',
              siglaDepartamento: 'LIC',
              link: null
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
              nome: 'ENGENHARIA DE SOFTWARE',
              codigoSigaa: 'CIC0105',
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
              nome: 'INFORMATICA APLICADA A EDUCACAO',
              codigoSigaa: 'CIC0158',
              creditos: ' 60h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'ESTÁGIO SUP LC 2 + SUPR EST LIC 1',
              codigoSigaa: 'CIC0214/17',
              creditos: ' 105h + 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'PRODUÇÃO CIENTIFICA NA LICENCIATURA EM COMPUTAÇÃO',
              codigoSigaa: 'CIC0223',
              creditos: ' 30h',
              siglaDepartamento: 'LIC',
              link: null
            },
            {
              nome: 'LÍNGUA DE SINAIS BRASILEIRA - BÁSICO',
              codigoSigaa: 'LIP0174',
              creditos: ' 60h',
              siglaDepartamento: 'LIP',
              link: null
            },
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
              nome: 'ADMINISTRAÇÃO DAS ORGANIZAÇÕES EDUCATIVAS',
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
            {
              nome: 'TOPICOS AVANCADOS EM COMPUTADORES',
              codigoSigaa: 'CIC0087',
              creditos: ' 60h',
              siglaDepartamento: 'CIC',
              link: null,
              tipo: 'OPT',
            },
          ]
        }
      ]
    }
  },
  methods: {
    gerarLinhas () {
    const array = [
      {inicio: 'CIC0004', fim: 'CIC0090', x1: null, x2: null, y1: null, y2: null },
      {inicio: 'CIC0090', fim: 'CIC0182', x1: null, x2: null, y1: null, y2: null },
      {inicio: 'MAT0025', fim: 'EST0022', x1: null, x2: null, y1: null, y2: null },
      {inicio: 'CIC0090', fim: 'CIC0197', x1: null, x2: null, y1: null, y2: null },
    ]
      for (let i = 0; i < array.length; i++) {
        const inicio = document.getElementsByClassName(array[i].inicio)
        const fim = document.getElementsByClassName(array[i].fim)
        this.connect(inicio, fim)
      }

    },
    getOffset (el)  {
      const rect = el[0].getBoundingClientRect();
      return {
        left: rect.left + window.pageXOffset,
        top: rect.top + window.pageYOffset,
        width: rect.width || el.offsetWidth,
        height: rect.height || el.offsetHeight
      };
    },
    connect (div1, div2)  {

      const elementos = document.getElementsByClassName('card-disciplina')
      const coordenadas = []
      for (let item of elementos) {
        coordenadas.push(item.getBoundingClientRect())
      }

      const htmlLine = "<div style='padding:0px; margin:0px; height: 2px; background-color:#000000; line-height:1px; position:absolute; left:" + cx + "px; top:" + cy + "px; width:" + length + "px; -moz-transform:rotate(" + angle + "deg); -webkit-transform:rotate(" + angle + "deg); -o-transform:rotate(" + angle + "deg); -ms-transform:rotate(" + angle + "deg); transform:rotate(" + angle + "deg);' />";
      document.body.innerHTML += htmlLine;
    }
  }
}
</script>

<style lang="scss">
  .arrow {
    position: absolute;
    z-index:10;
    width: 120px;
  }

  .line {
    margin-top: 14px;
    width: 90px;
    background: blue;
    height: 10px;
    float: left;
  }

  .point {
    width: 0;
    height: 0;
    border-top: 20px solid transparent;
    border-bottom: 20px solid transparent;
    border-left: 30px solid blue;
    float: right;
  }
</style>
