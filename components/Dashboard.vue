<template>
  <div class="pt-4 bg-gray-200">
    <div class="grid-rows-3 flex">
      <div class="flex-none w-80" />
      <div class="bg-gray-100 grow p-5">
        <div class="grid grid-cols-4 items-center">
          <img
            class="h-10 w-10"
            src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
            alt=""
          >
          <div class="flex flex-col text-center col-span-2">
            <p class="text-base font-medium">
              INTEGRATED COMMAND CENTER
            </p>
            <p class="text-base font-medium text-gray-500">
              PERUMDA TIRTA SAIL CRUISE PINK BEACH KOMODO
            </p>
          </div>
          <div />
        </div>
      </div>
      <div class="flex-none w-80 p-4">
        <div class="flex mt-3">
          <img
            class="inline-block h-10 w-10 rounded-full ring-2 ring-white"
            src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
            alt=""
          >
          <div class="flex flex-col ml-2">
            <p class="text-sm font-medium">
              Direktur
            </p>
            <p class="text-sm font-medium text-gray-500">
              Moch Anji Sumarn..
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Body -->
    <div class="grid-rows-3 flex bg-gray-200">
      <div class="flex-none w-80 pl-2">
        <div
          class="
            relative
            block
            p-4
            border border-gray-100
            rounded-xl
            mx-4
            bg-white
            my-4
          "
        >
          <div class="flex justify-between">
            <p class="text-xs font-light">
              Profit Bersih
            </p>
            <p class="text-xs font-normal">
              2%
            </p>
          </div>
          <p class="font-medium text-3xl">
            Rp250 Jt
          </p>
          <hr class="my-2">
          <div class="flex justify-between items-center">
            <p class="text-xs font-light">
              Pendapatan
            </p>
            <p class="text-base font-medium">
              Rp1,5M
            </p>
          </div>
        </div>

        <div
          class="
            relative
            block
            p-4
            border border-gray-100
            rounded-xl
            mx-4
            bg-white
            my-4
          "
        >
          <div class="flex justify-between">
            <p class="text-xs font-light">
              Profit Bersih
            </p>
            <font-awesome-icon :icon="['fas', 'xmark']" />
          </div>
          <div class="flex justify-between items-center">
            <p class="font-medium text-3xl my-3">
              82%
            </p>
            <p class="text-xs font-medium mr-3">
              18%
            </p>
          </div>
        </div>

        <div
          class="
            relative
            block
            p-4
            border border-gray-100
            rounded-xl
            mx-4
            bg-white
            my-4
          "
        >
          <div class="flex justify-between">
            <p class="text-xs font-light">
              Jumlah Pelanggan
            </p>
            <p class="text-xs font-normal">
              10%
            </p>
          </div>
          <p class="font-medium text-2xl">
            2.050
          </p>
          <hr class="my-2">
          <div class="grid grid-cols-2 items-center gap-2">
            <div class="flex flex-row place-items-center justify-between">
              <p class="text-xs font-light">
                Jumlah SR
              </p>
              <p class="text-base font-medium">
                2000
              </p>
            </div>
            <div class="flex flex-row place-items-center justify-between">
              <p class="text-xs font-light mr-1">
                Jumlah MBR
              </p>
              <p class="text-base font-medium">
                50
              </p>
            </div>
          </div>
        </div>

        <div
          class="
            relative
            block
            p-4
            border border-gray-100
            rounded-xl
            mx-4
            bg-white
            my-4
          "
        >
          <div class="flex justify-between">
            <p class="text-xs font-light">
              Pengaduan
            </p>
            <font-awesome-icon :icon="['fas', 'xmark']" />
          </div>
          <div class="flex justify-between items-center">
            <p class="font-medium text-3xl my-3">
              50%
            </p>
            <p class="text-xs font-medium mr-3">
              90%
            </p>
          </div>
          <p class="text-xs">
            Penyelesaian Pengaduan <span class="font-semibold">90.54%</span>
          </p>
        </div>

        <div
          class="
            relative
            block
            p-4
            border border-gray-100
            rounded-xl
            mx-4
            bg-white
            my-4
          "
        >
          <div class="flex justify-between">
            <p class="text-xs font-light">
              Tingkat Penyelesaian Pengaduan
            </p>
            <font-awesome-icon :icon="['fas', 'xmark']" />
          </div>
          <div class="grid grid-cols-2">
            <PieChart :data="barChartData" :height="400" />
            <div class="flex flex-col justify-center">
              <div class="flex flex-row justify-between items-center">
                <p class="text-xs font-light">
                  Pengaduan Selesai
                </p>
                <p class="text-xs font-light">
                  12
                </p>
              </div>
              <div class="flex flex-row justify-between items-center">
                <p class="text-xs font-light">
                  Pengaduan Belum Selesai
                </p>
                <p class="text-xs font-light">
                  21
                </p>
              </div>
            </div>
          </div>
        </div>

        <div
          class="
            grid
            h-28
            border-gray-400
            rounded-xl
            mx-4
            bg-gray-200
            my-4
            border-2 border-dashed
          "
        >
          <font-awesome-icon :icon="['fas', 'circle-plus']" class="h-8 w-8 fill-gray-500 place-self-center" />
        </div>
      </div>
      <div class="bg-white grow mt-4 rounded-xl">
        <div class="bg-green-400 mx-4 mt-4">
          <marquee behavior="" direction="">
            +1 Sambungan baru terpasang &emsp; +1 Pengaduan masuk
          </marquee>
        </div>
        <div class="grid grid-cols-3 gap-12 justify-between my-4 mx-6">
          <div class="p-4 bg-gray-100 rounded-lg">
            <p class="text-xs font-light">
              Luas Wilayah Administratif
            </p>
            <p class="text-4xl font-semibold mt-2">
              10 km<sup>2</sup>
            </p>
          </div>
          <div class="p-2 col-span-2 bg-gray-100 grid grid-cols-2 rounded-lg">
            <div class="flex place-items-center justify-between px-4">
              <div class="w-8 h-8 border rounded-full bg-red-400" />
              <p class="text-sm font-semibold w-32">
                Total Penduduk Terlayani
              </p>
              <div class="mr-2 text-right">
                <p class="text-base font-semibold">
                  2.050
                </p>
                <p class="text-xs font-semibold">
                  +50
                </p>
              </div>
            </div>
            <div class="flex place-items-center justify-between px-4">
              <div class="w-8 h-8 border rounded-full bg-red-400" />
              <p class="text-sm font-semibold w-32">
                Total Penduduk Belum Terlayani
              </p>
              <div class="mr-2 text-right">
                <p class="text-base font-semibold">
                  500
                </p>
                <p class="text-xs font-semibold">
&nbsp;
                </p>
              </div>
            </div>
          </div>
        </div>
        <div>
          <client-only>
            <l-map
              v-show="loadingMap"
              :zoom="zoom"
              :center="center"
              :options="{ zoomControl: false }"
              style="height: 70vh"
              class="rounded-bl-lg rounded-br-lg relative"
            >
              <l-tile-layer :url="url" :attribution="attribution" />
              <l-marker :lat-lng="markerLatLng">
                <l-popup>Hello!</l-popup>
              </l-marker>
              <l-control
                position="bottomleft"
              >
                <div class="w-full bg-white mb-6 mx-1.5 flex flex-row rounded-lg">
                  <div class="flex px-5 py-4">
                    <div class="px-2 h-8 border rounded-full bg-red-400 flex mr-2">
                      <p
                        class="text-center self-center font-semibold"
                        style="color:white;"
                      >
                        Rp
                      </p>
                    </div>
                    <div class="mr-4 mt-2">
                      <p class="text-sm font-semibold">
                        Total Sudah Bayar
                      </p>
                      <p class="text-base font-semibold">
                        Rp10.000.000
                      </p>
                      <p class="text-xs font-light">
                        <span
                          style="color:green;"
                        >190</span>/2.050 Pelanggan
                      </p>
                    </div>
                    <div
                      class="mt-2 flex "
                      style="color:green;"
                    >
                      <font-awesome-icon
                        :icon="['fas', 'arrow-up']"
                        class="mr-1 h-2 mt-1"
                      />
                      <p class="text-xs font-semibold">
                        10%
                      </p>
                    </div>
                  </div>

                  <div class="flex px-5 py-4">
                    <div class="px-2 h-8 border rounded-full bg-red-400 flex mr-2">
                      <p
                        class="text-center self-center font-semibold"
                        style="color:white;"
                      >
                        Rp
                      </p>
                    </div>
                    <div class="mr-4 mt-2">
                      <p class="text-sm font-semibold">
                        Total Sudah Bayar
                      </p>
                      <p class="text-base font-semibold">
                        Rp10.000.000
                      </p>
                      <p class="text-xs font-light">
                        <span
                          style="color:green;"
                        >190</span>/2.050 Pelanggan
                      </p>
                    </div>
                    <div
                      class="mt-2 flex "
                      style="color:green;"
                    >
                      <font-awesome-icon
                        :icon="['fas', 'arrow-up']"
                        class="mr-1 h-2 mt-1"
                      />
                      <p class="text-xs font-semibold">
                        10%
                      </p>
                    </div>
                  </div>

                  <div class="flex px-5 py-4">
                    <div class="px-2 h-8 border rounded-full bg-red-400 flex mr-2">
                      <p
                        class="text-center self-center font-semibold"
                        style="color:white;"
                      >
                        Rp
                      </p>
                    </div>
                    <div class="mr-4 mt-2">
                      <p class="text-sm font-semibold">
                        Total Sudah Bayar
                      </p>
                      <p class="text-base font-semibold">
                        Rp10.000.000
                      </p>
                      <p class="text-xs font-light">
                        <span
                          style="color:green;"
                        >190</span>/2.050 Pelanggan
                      </p>
                    </div>
                    <div
                      class="mt-2 flex "
                      style="color:green;"
                    >
                      <font-awesome-icon
                        :icon="['fas', 'arrow-up']"
                        class="mr-1 h-2 mt-1"
                      />
                      <p class="text-xs font-semibold">
                        10%
                      </p>
                    </div>
                  </div>
                </div>
              </l-control>
            </l-map>
          </client-only>
        </div>
      </div>
      <div class="bg-gray-200 flex-none w-80">
        <div class="flex flex-col border border-gray-400 mx-4 bg-white my-4">
          <div class="bg-gray-100 flex flex-col">
            <font-awesome-icon
              :icon="['fas', 'xmark']"
              class="self-end mt-2 mr-4"
            />
            <div class="flex justify-between items-center px-3 pb-2">
              <p class="text-base font-semibold">
                Work Order
              </p>
              <p class="text-xs font-semibold">
                01-01-21 15:00:00
              </p>
            </div>
            <hr>
          </div>
          <div class="px-3">
            <div class="flex justify-between items-center pt-2">
              <p class="text-base font-semibold">
                HBL 11111
              </p>
              <p class="text-xs font-light">
                01-01-21 15:00
              </p>
            </div>
            <p class="text-sm font-semibold py-1 w-52">
              Pressure blimbing 0.1 bar
            </p>
            <div class="w-8 h-8 border rounded-full bg-red-400" />
            <p class="text-xs font-semibold py-2">
              Belum ada penugasan
            </p>
          </div>
          <hr class="mx-2">
          <div class="px-3">
            <div class="flex justify-between items-center pt-2">
              <p class="text-base font-semibold">
                HBL 11112
              </p>
              <p class="text-xs font-light">
                01-01-21 07:00
              </p>
            </div>
            <p class="text-sm font-semibold py-1 w-52">
              Kerusakan Pipa Distribusi Wendit barat
            </p>
            <div class="flex items-center">
              <div class="w-8 h-8 border rounded-full bg-red-400 mr-1" />
              <div class="w-8 h-8 border rounded-full bg-red-400 mr-2" />
              <div>
                <p class="text-base font-semibold">
                  Suratno
                </p>
                <p class="text-xs font-semibold">
                  SPK 12345678
                </p>
              </div>
            </div>
            <p class="text-xs font-semibold py-2">
              Estimasi selesai 01-01-21 15:00
            </p>
          </div>
        </div>

        <div class="flex flex-col border border-gray-400 mx-4 bg-white my-4">
          <div class="bg-gray-100 flex flex-col">
            <font-awesome-icon
              :icon="['fas', 'xmark']"
              class="self-end mt-2 mr-4"
            />
            <div class="flex justify-between items-center px-3 pb-2">
              <p class="text-base font-semibold">
                Asset
              </p>
              <p class="text-xs font-semibold">
                01-01-21 15:00:00
              </p>
            </div>
            <hr>
          </div>
          <div class="px-3">
            <p class="text-sm font-semibold mt-2">
              Tekanan
            </p>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Wendit
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  4 bar
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Sawojajar
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  5 bar
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Blimbing
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  0.1 bar
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
          </div>
          <hr class="mx-2">
          <div class="px-3">
            <p class="text-sm font-semibold mt-2">
              Getaran
            </p>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Wendit
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  45 db
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Sawojajar
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  50 db
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
            <div class="flex justify-between items-center my-1">
              <p class="text-sm">
                Pompa Blimbing
              </p>
              <div class="flex justify-between items-center">
                <p class="text-xs">
                  102 db
                </p>
                <div class="w-4 h-4 border rounded-full bg-red-400 ml-3" />
              </div>
            </div>
          </div>
        </div>

        <div
          class="
            grid
            h-28
            border-gray-400
            rounded-xl
            mx-4
            bg-gray-200
            my-4
            border-2 border-dashed
          "
        >
          <font-awesome-icon :icon="['fas', 'circle-plus']" class="h-8 w-8 fill-gray-500 place-self-center" />
        </div>
      </div>
    </div>
    <Table />
  </div>
</template>

<script>
// import { XIcon, ViewGridAddIcon } from '@heroicons/vue/solid'

// import { PieChart } from 'vue-chart-3'
// import { Chart, registerables } from 'chart.js'
// import { ref } from 'vue'

// import { LMap, LTileLayer, LMarker, LPopup } from '@vue-leaflet/vue-leaflet'

// Chart.register(...registerables)

export default {
  name: 'DashboardPage',
  data () {
    return {
      barChartData: {
        labels: [],
        datasets: [
          {
            label: 'Visualizaciones',
            data: [2, 1],
            backgroundColor: ['#77CEFF', '#0079AF'],
            borderColor: '#FFFFFF',
            borderWidth: 1
          }
        ]
      },
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 17,
      center: [-8.650597625958902, 115.22229258179766],
      markerLatLng: [-8.650597625958902, 115.22229258179766],
      loadingMap: true
    }
  },
  // props: {
  //   msg: String,
  // },
  //   components: { XIcon, PieChart, ViewGridAddIcon, LMap, LTileLayer, LMarker, LPopup },
  mounted () {

  },
  async beforeMount () {
    // // HERE is where to load Leaflet components!
    // const { circleMarker } = await import("leaflet/dist/leaflet-src.esm");
    // // And now the Leaflet circleMarker function can be used by the options:
    // this.geojsonOptions.pointToLayer = (feature, latLng) =>
    //   circleMarker(latLng, { radius: 8 });
    // this.mapIsReady = true;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
