<template>
            <div class="accordion-item">
                <h2
                  class="accordion-header"
                  :id="schedule.id + 'heading'"
                  v-b-toggle:[schedule.collapseId]
                >
                  <div class="">
                    <h4 class="my-0">{{ schedule.name }}</h4>
                  </div>
                </h2>
                <b-collapse :id="schedule.collapseId">
                  <div class="accordion-body">
                    <table class="table table-hover">
                      <thead>
                        <th>Course</th>
                        <td></td>
                        <td></td>
                        <th>Credits</th>
                      </thead>
                      <tr v-for="s in schedule.classes" :key="s['Course ID']">
                        <td>{{s['Course ID']}}</td>
                        <td>
                          <span class="fw-bold"> {{s['Course Name']}} </span>
                        </td>
                        <td>
                          <span class="badge bg-primary"> {{s['Category']}} </span>
                        </td>
                        <td>{{s['Credit Hours']}}</td>
                      </tr>
                      <tr>
                        <td></td>
                        <td></td>
                        <td></td>
                        <td class="fw-bold"></td>
                      </tr>
                    </table>
                  </div>
                </b-collapse>
            </div>
</template>

<script>
export default {
    name: "SemesterSchedule",
  props: {
    schedule: Object,
  },
}
</script>

<style>

</style>