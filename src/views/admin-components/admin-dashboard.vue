<template>
    <div class="components-page-main-container p-3 cards-container">
        <h1>Welcome Admin!</h1>
        <div style="background-color: #D6DCE5; padding-bottom: 30px; align-items: center  ">

        
        <div class="card-one">
            <div class="top-content">
                <img width="100" height="100" src="https://img.icons8.com/dusk/100/students.png" alt="students"/>
                <h1 class="text-white">{{ alumniCount }}</h1>
            </div>
            <div class="bottom-content one">
                <h3 class="dashboard-bottom-title">Total Alumni</h3>
                <i class="fa fa-arrow-circle-right" aria-hidden="true"></i>
            </div>
        </div>
        <div class="card-two">
            <div class="top-content">
                <img width="100" height="100" src="https://img.icons8.com/dusk/64/contact-card.png" alt="contact-card"/>
                <h1 class="text-white">4</h1>
            </div>
            <div class="bottom-content two">
                <h3 class="dashboard-bottom-title">Contact Support</h3>
                <i class="fa fa-arrow-circle-right" aria-hidden="true"></i>
            </div>
        </div>
        <!-- <div class="card-three">
            <div class="top-content">
                <img width="100" height="100" src="https://img.icons8.com/external-flaticons-lineal-color-flat-icons/100/external-courses-recruitment-agency-flaticons-lineal-color-flat-icons-2.png" alt="external-courses-recruitment-agency-flaticons-lineal-color-flat-icons-2"/>
                <h1 class="text-white">7</h1>
            </div>
            <div class="bottom-content three">
                <h3 class="dashboard-bottom-title">Courses</h3>
                <i class="fas fa-circle-right"></i>
                <i class="fa fa-arrow-circle-right" aria-hidden="true"></i>
            </div>
        </div> -->
        <div class="card-four">
            <div class="top-content">
                <img width="100" height="100" src="https://img.icons8.com/external-flaticons-lineal-color-flat-icons/100/external-courses-recruitment-agency-flaticons-lineal-color-flat-icons-2.png" alt="external-courses-recruitment-agency-flaticons-lineal-color-flat-icons-2"/>
                <h1 class="text-white">7</h1>
            </div>
            <div class="bottom-content four">
                <h3 class="dashboard-bottom-title">Pending Approval</h3>
                <i class="fas fa-circle-right"></i>
                <i class="fa fa-arrow-circle-right" aria-hidden="true"></i>
            </div>
        </div>

    </div>

    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { db } from '../../firebase/index.js'
import { collection, getDocs } from 'firebase/firestore'

const alumniCount = ref(0)

const fetchAlumniCount = async () => {
  try {
    const q = collection(db, 'users')
    const querySnapshot = await getDocs(q)
    let count = 0
    querySnapshot.forEach(doc => {
      const userData = doc.data()
      if (userData.hasOwnProperty('userlevel') && userData.userlevel === 'alumni') {
        count++
      }
    })
    alumniCount.value = count
  } catch (error) {
    console.error('Error fetching alumni count:', error.message)
  }
}

onMounted(() => {
  fetchAlumniCount()
})
</script>