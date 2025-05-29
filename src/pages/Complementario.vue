<template>
  <div class="curso-main-container complementario">
    <BannerInterno
      icono="far fa-folder-open"
      titulo="Material complementario"
    ></BannerInterno>
    <div class="container tarjeta tarjeta--blanca p-4 p-md-5 mb-5">
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th colspan="3" scope="col">Tema</th>
              <th colspan="5" scope="col">Referencia APA del material</th>
              <th colspan="2" scope="col">Tipo</th>
              <th colspan="2" scope="col">Enlace</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(item, index) in computedData"
              :key="'complementario-' + index"
            >
              <td
                class="text-start"
                colspan="3"
                scope="row"
                v-html="item.tema"
              ></td>
              <td
                class="text-start"
                colspan="5"
                scope="row"
                v-html="item.referencia"
              ></td>
              <td colspan="2" v-html="item.tipo"></td>
              <td colspan="2">
                <div class="complementario__enlaces">
                  <a
                    v-for="(link, linkIndex) of item.link"
                    :key="linkIndex"
                    class="complementario__btn"
                    :href="link"
                    target="_blank"
                    ><i class="fas fa-external-link-alt"></i
                  ></a>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'MaterialComplementario',
  computed: {
    complementarioData() {
      return [
        {
          tema: 'Internet de las cosas (IoT) en agricultura',
          referencia:
            'Farmonaut. (2023). <i>Revolutionizing Agriculture: How IoT and Drones Are Driving Precision Farming for Sustainable Crop Yields</i>. Farmonaut.',
          tipo: 'Documento Técnico',
          link:
            'https://farmonaut.com/precision-farming/revolutionizing-agriculture-how-iot-and-drones-are-driving-precision-farming-for-sustainable-crop-yields/ ',
        },
        {
          tema: 'Automatización con sistemas SCADA',
          referencia:
            'GAO. (2023). Precision Agriculture: Benefits and Challenges for Technology Adoption and Use. U.S. Government Accountability Office',
          tipo: 'Documento Técnico',
          link: 'https://www.gao.gov/products/gao-24-105962 ',
        },
        {
          tema: 'Drones en la agricultura',
          referencia:
            'Farmonaut. (2023). How Data-Driven Precision Farming and IoT are Optimizing Crop Yields and Sustainability. Farmonaut',
          tipo: 'Documento Técnico',
          link:
            'https://farmonaut.com/precision-farming/revolutionizing-agriculture-how-data-driven-precision-farming-and-iot-are-optimizing-crop-yields-and-sustainability/ ',
        },
        {
          tema: 'GNSS en la agricultura',
          referencia:
            'Armonaut. (2006). UN-Zambia-ESA <i>Regional Workshop on the Applications of GNSS in Sub-Saharan Africa</i> - June 2006.',
          tipo: 'Documento Técnico',
          link:
            'https://www.unoosa.org/documents/pdf/psa/activities/2006/zambia/presentations/04-01-01.pdf ',
        },
        {
          tema: 'Gestión integrada de fincas con LiteFarm',
          referencia:
            'LiteFarm. (2021). Sustainable farm management tool. FAO.',
          tipo: 'Herramienta de gestión ',
          link: 'https://www.litefarm.org/ ',
        },
        {
          tema: 'Gestión eficiente del agua con AquaCrop-OS',
          referencia:
            'Foster, T., et al. (2017). <i>AquaCrop-OS: Opensource version of FAO&#8242;s water productivity model.</i>',
          tipo: 'Simulador',
          link: 'https://digitalcommons.unl.edu/wffdocs/16/ ',
        },
        {
          tema: 'Simulador CropSyst para manejo de cultivos',
          referencia:
            '<i>Farmonaut. (2023). Using Drones for Precision Agriculture. Farmonaut.</i>',
          tipo: 'Simulador',
          link:
            'https://www.fao.org/land-water/land/land-governance/land-resources-planning-toolbox/category/details/en/c/1236450/ ',
        },
      ]
    },
    computedData() {
      const data = this.complementarioData
      return data.map(item => {
        let nuevoLink = []
        if (item.link) {
          if (typeof item.link === 'string') {
            nuevoLink.push(item.link)
          } else {
            nuevoLink = item.link
          }
        } else if (item.descarga) {
          if (typeof item.descarga === 'string') {
            nuevoLink.push(this.obtenerLink(item.descarga))
          } else {
            item.descarga.forEach(link => {
              nuevoLink.push(this.obtenerLink(link))
            })
          }
        }
        return {
          ...item,
          link: nuevoLink,
        }
      })
    },
  },
}
</script>

<style lang="sass">
.complementario
  &__enlaces
    display: flex
    justify-content: center
    flex-wrap: wrap
    a
      margin: 0 5px
  &__btn
    font-size: 1.5em
    line-height: 1em
table
  width: calc(100% - 1px)
  min-width: 800px
  thead
    background-color: $color-sistema-e
    th
      border-color: $color-sistema-e
  th, td
    padding: 25px 20px
    text-align: center
</style>
