<template>
  <div id="app" class="d-flex flex-column min-vh-100">
    <!-- Main Content -->
    <main class="flex-fill">
      <div class="container-fluid">
        <div class="row mb-5">
          <h1>Degree Planner</h1>
        </div>
        <div class="row main-content">
          <!-- Classes -->
          <div class="col-lg-4 required-classes">
            <h3>Required Classes</h3>

            <b-tabs content-class="mt-3">
              <!-- LAC Requirements -->

              <b-tab title="LAC" active>
                <div id="lac">
                  <div class="my-4 text-left" id="lac-reqs">
                    <CourseInfoCard :course=c  v-for="c in lacCourses" :key="c['Course ID']" />
                  </div>
                </div>
              </b-tab>
              <!-- CS Requirements -->
              <b-tab title="CS" active>
                <div id="csis">
                  <CourseInfoCard :course=d  v-for="d in csisCourses" :key="d['Course ID']" />
                </div>
              </b-tab>
            </b-tabs>
          </div>

          <!-- Semester Schedules -->
          <div class="col-lg-6 semester-schedules">
            <h3>Semester Schedules</h3>

            <SemesterSchedule :schedule=s v-for="s in schedules" :key="s.id" 
            class="accordion my-4" id="s.id"/>
              
          </div>

          <!-- Table of Contents Sidebar -->
          <div class="col-lg-2 position-sticky top-0 h-100 ps-5 toc">
            <nav>
              <p class="text-muted">On this page</p>
              <ul>
                <li><a href="#fall2020">Fall 2020</a></li>
                <li><a href="#spring2021">Spring 2021</a></li>
                <li><a href="#fall2021">Fall 2021</a></li>
                <li><a href="#spring2022">Spring 2022</a></li>
                <li><a href="#fall2022">Fall 2022</a></li>
                <li><a href="#spring2023">Spring 2023</a></li>
                <li><a href="#fall2023">Fall 2023</a></li>
                <li><a href="#spring2024">Spring 2024</a></li>
              </ul>
            </nav>
          </div>
        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer class="bg-dark text-light py-4">
      <div class="container-fluid">
        <div class="row">
          <div class="col">
            <p>Made with ❤️ by FHU students!</p>
          </div>

          <div class="col-md-3">
            <p>&copy; 2021 Freed-Hardeman University</p>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import CourseInfoCard from './components/CourseInfoCard.vue'
import lacCoursesFromFile from './lac.json'
import csisCoursesFromFile from './csis.json'
import SemesterSchedule from './components/SemesterSchedule.vue';

export default {
  name: "App",
  components: {
    CourseInfoCard,
    SemesterSchedule
  },
  mounted() {

  },
  data() {
    return {
      schedules: [
        {
          name: "Fall 2020",
          id: "fall2020",
          collapseId: "fall2020schedule",
          classes: [],
        },
        {
          name: "Spring 2021",
          id: "spring2020",
          collapseId: "spring2020schedule",
          classes: [],
        },
        {
          name: "Fall 2021",
          id: "fall2021",
          collapseId: "fall2021schedule",
          classes: [],
        },
        {
          name: "Spring 2022",
          id: "spring2022",
          collapseId: "spring2022schedule",
          classes: [],
        },
        {
          name: "Fall 2022",
          id: "fall2022",
          collapseId: "fall2022schedule",
          classes: [],
        },
        {
          name: "Spring 2023",
          id: "spring2023",
          collapseId: "spring2023schedule",
          classes: [],
        },
        {
          name: "Fall 2023",
          id: "fall2023",
          collapseId: "fall2023schedule",
          classes: [],
        },
        {
          name: "Spring 2024",
          id: "spring2024",
          collapseId: "spring2024schedule",
          classes: [],
        }
      ],
      courses: [],

      lacCourses: lacCoursesFromFile,
      csisCourses: csisCoursesFromFile,
    };
  },

};
</script>

<style>
#app {
  font-family: "Nunito Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.toc nav {
  text-align: left;
}

.toc ul {
  padding: 0;
  list-style: none;
}

.toc li {
  margin: 0;
  margin-bottom: 0.5rem;
}

.toc li a {
  text-decoration: none;
}

.toc li a:hover {
  text-decoration: underline;
}

.required-classes .card {
  border-left: 8px solid #0c63e4;
}
</style>
