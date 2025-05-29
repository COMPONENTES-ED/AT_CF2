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
  computed: {
    referenciasData() {
      return [
        {
          referencia:
            'Aguilera, M. (2014). Desarrollo en la Avicultura en Colombia: Instituciones, Organizaciones y Tecnología. Revista del Banco de la República, 87(1046), 21–56.',
        },
        {
          referencia:
            'Bernal, E. J. A., & Díaz, A. (2014). Mico CORPOICA: Buenas Prácticas Agrícolas (BPA) en el Cultivo de Aguacate. Bogotá: CORPOICA.',
        },
        {
          referencia: 'FAO. (2023). <i>Simulation Model</i>',
          link:
            'https://www.fao.org/land-water/land/land-governance/land-resources-planning-toolbox/category/details/en/c/1236450/.',
        },
        {
          referencia:
            'Farmonaut. (2023). Revolution culture: How IoT and Drones Are Driving Precision Farming for Sustainable Crop Yields. ',
          link: 'https://farmonaut.com/iot-precision-agriculture/',
        },
        {
          referencia:
            'Food and Agriculture Organization of the United Nations. (2006). Evapotranspiración del Cultivo: Guías para determinación de los requerimientos de agua de los cultivos (Estudios FAO: Riego y Drenaje). <i>Food & Agriculture Organization.</i> ',
          link: 'https://www.fao.org',
        },
        {
          referencia:
            'Pieri, R. (2010). Metodología de la Investigación (5ª ed.). McGraw-Hill Interamericana.',
        },
        {
          referencia:
            'Fundación Al. (2015). Manual de manejo integrado de plagas: Guía para cuidar un huerto orgánico y saludable. Bolivia: Fundación Alternativas.',
        },
        {
          referencia:
            'Fundación Alternativas. (2015). Agricultura Urbana en Cursos: Estrategias para la resiliencia y sostenibilidad. Bolivia: Fundación Alternativas.',
        },
        {
          referencia:
            'Fundación Alternativas. (2015). Manejo de Plagas en la Agricultura Orgánica. La Paz: Fundación Alternativa.',
        },
        {
          referencia:
            'Garbanzo, M. (2011). Manual de buenas prácticas para el Cultivo de Aguacate Hass. Costa Rica: CORFOGA.',
        },
        {
          referencia:
            'Instituto Agropecuario (ICA). (2012). Manejo Fitosanitario del Cultivo del Aguacate Hass. Bogotá: ICA.',
        },
        {
          referencia: 'LiteFarm. (2021). L Farm Management Tool.',
          link: 'https://www.litefarm.org/',
        },
        {
          referencia:
            'U.S. Government Accountability Office. (2023). Agriculture Technologies for Resource Efficiency*.',
          link: 'https://www.gao.gov/products/gao-24-105962',
        },
      ]
    },
    orderedData() {
      const ArrayOrdered = [...this.referenciasData].sort((a, b) => {
        const afl = this.quitarAcentos(a.referencia.split(' ')[0].toLowerCase())
        const bfl = this.quitarAcentos(b.referencia.split(' ')[0].toLowerCase())
        if (afl < bfl) return -1
        if (afl > bfl) return 1
        return 0
      })
      return ArrayOrdered
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
