<template>
  <div class="bg-white rounded-xl p-4">
    <div class="flex justify-between">
      <p class="text-xl font-semibold">
        Pengerjaan
      </p>
      <font-awesome-icon :icon="['fas', 'xmark']" class="self-end mt-2 mr-4" />
    </div>
    <div class="flex justify-between mt-8">
      <div class="flex bg-gray-300 px-4 rounded-md">
        <p class="p-4 font-semibold">
          Belum ditugaskan: <span class="text-xl ">1</span>
        </p>
        <p class="p-4 font-semibold">
          Sedang dikerjakan: <span class="text-xl">1</span>
        </p>
      </div>
      <div class="flex bg-gray-300 px-4 rounded-md">
        <p class="p-4 font-semibold">
          Pekerjaan Selesai: <span class="text-xl ">10</span>
        </p>
      </div>
    </div>
    <div class="mt-4">
      <table style="width: 100%" class="border-collapse border border-white">
        <thead>
          <tr class="bg-blue-900  rounded-t-xl w-full border border-white">
            <th v-for="(col,i) in cols" :key="col" :class="'font-normal leading-10 text-white px-2 '+col.class " @click="sortTable(i)">
              {{ col.value }}
              <font-awesome-icon :icon="['fas', 'up-down']" />
            </th>
          </tr>
        </thead>
        <tbody cellspacing="4">
          <tr v-for="(row,i) in get_rows()" :key="i" class=" bg-gray-100 px-6 py-4 border border-white">
            <td v-for="(r, j) in row" :key="j">
              <div :class="r.class">
                {{ r.value }}
              </div>
            </td>
          </tr>
        </tbody>
      </table>
      <div class="flex justify-between bg-gray-100 px-6 py-3">
        <div class="flex items-center">
          <p class="mr-2">
            Data yang ditampilkan
          </p>
          <select v-model="elementsPerPage" class="font-semibold bg-gray-100" @change="change_element_per_page($event)">
            <option value="1">
              1
            </option>
            <option value="2">
              2
            </option>
          </select>
        </div>
        <div class="flex items-center ">
          <div
            class="mx-3 font-semibold"
            @click="change_page(i)"
          >
            <font-awesome-icon
              :icon="['fas', 'angle-left']"
              class="self-end h-3"
            /> Prev
          </div>
          <div
            v-for="i in num_pages()"
            :key="i"
            :class="[i == currentPage ? 'font-semibold' : '']+' mx-3'"
            @click="change_page(i)"
          >
            {{ i }}
          </div>
          <div
            class="mx-3 font-semibold"
            @click="change_page(i)"
          >
            Next
            <font-awesome-icon
              :icon="['fas', 'angle-right']"
              class="self-end h-3"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'TableComponent',
  data () {
    return {
      currentPage: 1,
      elementsPerPage: 1,
      ascending: false,
      sortColumn: '',
      cols: [
        {
          value: 'Pengerjaan',
          class: 'text-left'
        }, {
          value: 'Tanggal',
          class: 'text-center'
        }, {
          value: 'Nama SPK',
          class: 'text-left'
        }, {
          value: 'Pengaduan',
          class: 'text-center'
        }, {
          value: 'Lokasi',
          class: 'text-center'
        }, {
          value: 'Detail',
          class: 'text-center'
        }, {
          value: 'Estimasi Selesai',
          class: 'text-center'
        }, {
          value: 'Penanggung Jawab',
          class: 'text-center'
        }
      ],
      rows: [
        [
          {
            value: 'Belum ditugaskan',
            class: 'mx-auto font-normal text-white text-sm py-1 rounded-full m-2 text-center w-max px-4 ' + (this.elementsPerPage > 1 ? 'bg-red-500' : this.elementsPerPage > 2 ? 'bg-yellow-500' : 'bg-green-500')
          },
          {
            value: '21 Juli 2021',
            class: 'text-center'
          },
          {
            value: 'HBL 124',
            class: ''
          },
          {
            value: 'Kerusakan Aset',
            class: ''
          },
          {
            value: 'Blimbing',
            class: ''
          },
          {
            value: 'Tekanan pipa 0.1',
            class: ''
          },
          {
            value: '-',
            class: ''
          },
          {
            value: 'Belum ada penugasan',
            class: ''
          }
        ],
        [
          {
            value: 'Sedang dikerjakan',
            class: 'mx-auto font-normal text-white text-sm py-1 rounded-full m-2 text-center w-max px-4 ' + (this.elementsPerPage < 1 ? 'bg-red-500' : this.elementsPerPage < 2 ? 'bg-yellow-500' : 'bg-green-500')
          },
          {
            value: '11 Juli 2021',
            class: 'text-center'
          },
          {
            value: 'HBL 123',
            class: ''
          },
          {
            value: 'Kerusakan Aset',
            class: ''
          },
          {
            value: 'Blimbing',
            class: ''
          },
          {
            value: 'Tekanan pipa 0.1',
            class: ''
          },
          {
            value: '-',
            class: ''
          },
          {
            value: 'Belum ada penugasan',
            class: ''
          }
        ]

      ]

    }
  },
  computed: {

  },
  methods: {
    sortTable: function sortTable (col) {
      if (this.sortColumn === col) {
        this.ascending = !this.ascending
      } else {
        this.ascending = true
        this.sortColumn = col
      }

      const ascending = this.ascending

      this.rows.sort(function (a, b) {
        if (a[col].value > b[col].value) {
          return ascending ? 1 : -1
        } else if (a[col].value < b[col].value) {
          return ascending ? -1 : 1
        }
        return 0
      })
    },
    num_pages: function numPages () {
      return Math.ceil(this.rows.length / this.elementsPerPage)
    },
    get_rows: function getRows () {
      const start = (this.currentPage - 1) * this.elementsPerPage
      const end = start + this.elementsPerPage
      return this.rows.slice(start, end)
    },
    change_page: function changePage (page) {
      this.currentPage = page
    },
    change_element_per_page: function changeElementPerPage (event) {
      this.elementsPerPage = event.target.value
      this.get_rows()
      this.num_pages()
    }
  }
}
</script>
<style scoped>
/* table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  cursor: pointer;
  padding: 8px;
  min-width: 30px;
}
table th:hover {
        background: #717699;
      }
table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
}

table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  cursor: pointer;
  padding: 8px;
  min-width: 30px;
}
table th:hover {
        background: #717699;
      }
table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
} */

.pagination {
  font-family: 'Open Sans', sans-serif;
  text-align: right;
  width: 750px;
  padding: 8px;
}

.arrow_down {
  background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB8AAAAaCAYAAABPY4eKAAAAAXNSR0IArs4c6QAAAvlJREFUSA29Vk1PGlEUHQaiiewslpUJiyYs2yb9AyRuJGm7c0VJoFXSX9A0sSZN04ULF12YEBQDhMCuSZOm1FhTiLY2Rky0QPlQBLRUsICoIN/0PCsGyox26NC3eTNn3r3n3TvnvvsE1PkwGo3yUqkkEQqFgw2Mz7lWqwng7ztN06mxsTEv8U0Aam5u7r5EInkplUol/f391wAJCc7nEAgE9Uwmkzo4OPiJMa1Wq6cFs7Ozt0H6RqlUDmJXfPIx+qrX69Ti4mIyHA5r6Wq1egND+j+IyW6QAUoul18XiUTDNHaSyGazKcZtdgk8wqhUKh9o/OMvsVgsfHJy0iWqVrcQNRUMBnd6enqc9MjISAmRP3e73T9al3XnbWNjIw2+KY1Gc3imsNHR0YV4PP5+d3e32h3K316TySQFoX2WyWR2glzIO5fLTSD6IElLNwbqnFpbWyO/96lCoai0cZjN5kfYQAYi5H34fL6cxWIZbya9iJyAhULBHAqFVlMpfsV/fHxMeb3er+Vy+VUzeduzwWC45XA4dlD/vEXvdDrj8DvURsYEWK3WF4FA4JQP9mg0WrHZbEYmnpa0NxYgPVObm5teiLABdTQT8a6vrwdRWhOcHMzMzCiXlpb2/yV6qDttMpkeshEzRk4Wo/bfoe4X9vb2amzGl+HoXNT29vZqsVi0sK1jJScG+Xx+HGkL4Tew2TPi5zUdQQt9otPpuBk3e0TaHmMDh1zS7/f780S0zX6Yni+NnBj09fUZUfvudDrNZN+GkQbl8Xi8RLRtHzsB9Hr9nfn5+SjSeWUCXC7XPq5kw53wsNogjZNohYXL2EljstvtrAL70/mVaW8Y4OidRO1/gwgbUMvcqGmcDc9aPvD1gnTeQ+0nmaInokRj0nHh+uvIiVOtVvt2a2vLv7Ky0tL3cRTXIcpPAwMDpq6R4/JXE4vFQ5FI5CN+QTaRSFCYc8vLy1l0rge4ARe5kJ/d27kYkLXoy2Jo4C7K8CZOsEBvb+9rlUp1xNXPL7v3IDwxvPD6AAAAAElFTkSuQmCC')
}
.arrow_up {
  background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAaCAYAAACgoey0AAAAAXNSR0IArs4c6QAAAwpJREFUSA21Vt1PUmEYP4dvkQ8JFMwtBRocWAkDbiqXrUWXzU1rrTt0bdVqXbb1tbW16C9IBUSmm27cODdneoXjputa6069qwuW6IIBIdLvdaF4OAcOiGeDc87zPs/vd57P96WpFq7p6enbGo1mjKZpeTabjU1MTCRagGnOZHFxcXxtbe1XKpUq7+zslJeXl//Mz8+Hy+Uy3RxSE9qTk5M3otFooVQqgef4Wl9f343FYoEmoISrxuNxFX5f9vb2jhn/PxUKhfLS0tIPfFifUESRUMV8Pv/M6XReRm5rTGQyGeXxeGxYe1ezeBpBOBx2rKysbO7v79d4Wy3Y2Nj4GQqFbgnhaugxwiuGJx99Pp9FLBbXxYTXvTqd7v3MzIy6riIWGxJnMpl7AwMD14xGYyMsSq1WUyQdUqn0eSPlusQIsbGrq+vl4OCgvhFQZd1utyv1en0gEolcqsi47nWJlUrlG5fLZVcoFFy2nDKSDpIWlUoVTCQSEk4lCHmJMZ2GTCbTiMVikfIZ88l7enoos9l8dXt7+z6fDicxSJUokqDX6xXcl2wCROoc0vQCWL3sNfLOSdzR0fHY4XC4tVotl40gmVwup9xuN4OQv+UyqCFGH9rg7SOGYVRcBs3IEG4J0nVnamrqOtvuBDGGgQg9+wHFcVEi4a0LNkbdd6TrPKo8ODc311mteIIYjT/a398/jK+s1jnVM0kXoufCFvq0GuiIGEVgQIhfoygM1QrteEa9dAL7ITiYCt4RMabOK5AyKKzKWtvupLcRciu8D5J0EuDDPyT/Snd39yh6VtY2NhYQSR9G79Ds7OxdskRjEyAufvb7/cPoO5Z6e1+xtVKrq6vfcFzyi/A3ZrPZ3GdNSlwgo5ekE4X2RIQGf2C1WlufFE0GBeGWYQ8YERWLxQtnUVB830MKLZfL9RHir8lkssCn2G751tZWEWe03zTKm15YWPiEiXXTYDB0Ig/t7yd8PRws4EicwWHxO4jHD8/C5HiTTqd1BwcHFozKU89origB+y/kmzgYpgOBQP4fGmUiZmJ+WNgAAAAASUVORK5CYII=')
}
.arrow {
  float: right;
  width: 12px;
  height: 15px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position-y: bottom;
}

.number {
  display: inline-block;
  padding: 4px 10px;
  color: #FFF;
  border-radius: 4px;
  background: #44475C;
  margin: 0px 5px;
  cursor: pointer;
}
.number:hover, .number.active {
  background: #717699;
}
</style>
