<template>
  <div class="todo">
    <div class="container">
      <div class="row header mb-5 p-3">
        <div class="col-lg-12">
          <h2>What I do Today?</h2>
        </div>
      </div>
      <div class="row content">
        <div class="col-lg-12">
          <div class="pekerjaan-rumah">
            <div class="row">
              <div class="tugas col-lg-12 mb-4 text-start" v-for="tugasSaya in tugas" v-bind:key="tugasSaya.id">
                <ItemTugas v-bind:tugasSaya = "tugasSaya" @clicked="updateStatus($event, tugasSaya.id)" />
              </div>              
            </div>
          </div>          
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import 'bootstrap/dist/css/bootstrap.css'
import ItemTugas from "../components/ItemTugas.vue";

export default {
  name: 'TodoView',
  data: function() {
    return {
      tugas: [
        {
          id: 1,
          namaTugas: "Membersihkan Toilet",
          isDone: false
        },
        {
          id: 2,
          namaTugas: "Mencuci Baju",
          isDone: false
        },
        {
          id: 3,
          namaTugas: "Istirahat 8 Jam",
          isDone: false
        },
        {
          id: 4,
          namaTugas: "Upgrade Skill",
          isDone: false
        }
      ]
    }
  },
  components: {
    ItemTugas
  },
  methods: {
    updateStatus(event, val) {
      this.tugas.filter(function (t) {
        if (t.id == val) {
          return t.isDone = event;
        }
      });
    }
  }
}
</script>

<style scoped>
.header {
  background: #1abc9c;
}
.header h2 {
  margin: 0;
}

.tugas .item {
  font-size: 20px;
}
</style>
