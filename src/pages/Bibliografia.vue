<template>
  <div class="curso-main-container referencias">
    <BannerInterno
      icono="fas fa-book"
      titulo="Referencias bibliográficas"
    ></BannerInterno>
    <div class="container tarjeta tarjeta--blanca p-4 p-md-5 mb-5">
      <div v-for="ref in orderedData" :key="ref.link" class="referencias__item">
        <span v-html="ref.referencia"></span
        ><a v-if="ref.link" class="ms-1" :href="ref.link" target="_blank"
          ><span v-html="ref.link"></span
          ><i class="ms-1 fas fa-external-link-alt"></i
        ></a>
        <hr class="my-3" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Referencias',
  data: () => ({
    referencias: [
      {
        referencia:
          'Alternativascc.org. (n.d.). [Documento PDF]. Recuperado el 17 de junio de 2025, de',
        link:
          'https://alternativascc.org/wp-content/uploads/2018/05/mip_web-1.pdf',
      },
      {
        referencia:
          'CropSyst. (n.d.). [Simulador Web]. Fao.org. Recuperado el 17 de junio de 2025, de',
        link:
          'https://www.fao.org/land-water/land/land-governance/land-resources-planning-toolbox/category/details/en/c/1236450/ ',
      },
      {
        referencia:
          'Edu.co. (n.d.). [Documento PDF]. Recuperado el 16 de junio de 2025, de',
        link:
          'https://repositorio.unibague.edu.co/entities/publication/80fffeba-5ef1-4896-b721-e56c29b32bfa',
      },
      {
        referencia:
          'Fao.org. (n.d.). [Documento PDF]. Recuperado el 17 de junio de 2025, de',
        link:
          'https://openknowledge.fao.org/server/api/core/bitstreams/f3660258-d07f-487e-b3c1-01661c83cb16/content',
      },
      {
        referencia:
          'Foster, T., Brozović, N., Butler, A., Neale, C., Raes, D., Steduto, P., Fereres, E., & Hsiao, T. (2017). AquaCrop-OS: An open source version of FAO’s crop water productivity model. Agricultural Water Management, 181, 18–22. [Simulador Web].',
        link: 'https://doi.org/10.1016/J.AGWAT.2016.11.015',
      },
      {
        referencia:
          'Gov.co. (n.d.). [Documento PDF].  Recuperado el 17 de junio de 2025,  de',
        link:
          'https://www.banrep.gov.co/sites/default/files/publicaciones/archivos/dtser_214.pdf',
      },
      {
        referencia:
          'Government Accountability Office. (n.d.). Precision agriculture: Benefits and challenges for technology adoption and use. [Pagina Web]. Gao.gov. Recuperado el 16 de junio de 2025, de',
        link: 'https://www.gao.gov/products/gao-24-105962',
      },
      {
        referencia:
          'How IoT drives data-driven precision farming. (2024). [Pagina Web]. Farmonaut®.',
        link:
          'https://farmonaut.com/precision-farming/revolutionizing-agriculture-how-data-driven-precision-farming-and-iot-are-optimizing-crop-yields-and-sustainability/',
      },
      {
        referencia:
          'Metternicht, G. (n.d.). Use of remote sensing and GNSS in precision agriculture. [Documento PDF]. Unoosa.org. Recuperado el 16 de junio de 2025, de',
        link:
          'https://www.unoosa.org/documents/pdf/psa/activities/2006/zambia/presentations/04-01-01.pdf',
      },
      {
        referencia:
          'Montoya, E. A. Q., Universidad del Quindío, Cra. 15 Cll. 12 norte, 630004, Armenia, Colombia, Colorado, S. F. J., Muñoz, W. Y. C., Golondrino, G. E. C., Universidad del Quindío, Cra. 15 Cll. 12 norte, 630004, Armenia, Colombia, Universidad del Quindío, Cra. 15 Cll. 12 norte, 630004, Armenia, Colombia, & Institución universitaria Colegio Mayor del Cauca, Cra. 7 #2-34, 190003, Popayán, Colombia. (2017). Propuesta de una Arquitectura para Agricultura de Precisión Soportada en IoT. RISTI - Revista Ibérica de Sistemas e Tecnologias de Informação, 24, 39–56.',
        link: 'https://doi.org/10.17013/risti.24.39-56',
      },
      {
        referencia:
          'Smart farming with drones & IoT precision sensors. (2024). [Pagina Web]. Farmonaut®.',
        link:
          'https://farmonaut.com/precision-farming/revolutionizing-agriculture-how-iot-and-drones-are-driving-precision-farming-for-sustainable-crop-yields/ ',
      },
    ],
  }),
  computed: {
    orderedData() {
      return [...this.referencias].sort((a, b) => {
        const afl = this.quitarAcentos(a.referencia.split(' ')[0].toLowerCase())
        const bfl = this.quitarAcentos(b.referencia.split(' ')[0].toLowerCase())
        if (afl < bfl) return -1
        if (afl > bfl) return 1
        return 0
      })
    },
  },
  methods: {
    quitarAcentos(str) {
      return str.normalize('NFD').replace(/[\u0300-\u036f]/g, '')
    },
  },
}
</script>

<style lang="sass">
.referencias
  &__item
    &:last-child
      hr
        display: none
    a
      color: $blue
      text-decoration: underline
      overflow-wrap: break-word
</style>
