<template>
  <div>
    <q-carousel
        swipeable
        animated
        v-model="slide"
        infinite
        arrows
        autoplay
        v-model:fullscreen="fullscreen"
        style="background-color:var(--light-green)"
        height="70vh"
      >
        <q-carousel-slide class="row justify-center items-center" v-for="design in designs" :key="design.url" :name="design.no" >
          <q-img
            :src="design.url"
            fit="scale-down"
            spinner-color="primary"
            spinner-size="82px"
          >
            <div class="absolute-bottom text-subtitle2">
                {{design.name}} - {{ design.year }}
            </div>
          </q-img>
        </q-carousel-slide>
        <template v-slot:control>
          <q-carousel-control
            position="bottom-right"
            :offset="[18, 18]"
          >
            <q-btn
              push round dense color="white" text-color="primary"
              :icon="fullscreen ? 'fullscreen_exit' : 'fullscreen'"
              @click="fullscreen = !fullscreen"
            />
          </q-carousel-control>
        </template>
    </q-carousel>
    <q-list class="q-mt-md" bordered>
      <q-item v-for="project in projects" :key="project.name" class="column q-gutter-md q-mb-xl" >
        <div class="row justify-center q-gutter-md" >
          <q-item-section class="col-12 row justify-center" style="width:400px">
            <q-img
              :src="project.pictureUrl"
              :ratio="16/9"
              spinner-color="primary"
              spinner-size="82px"
              img-class="my-img"
            />
          </q-item-section>
          <div class="col-12">
            <q-item-section class="text-h6 text-bold">{{project.name}}</q-item-section>
            <q-item-section class="text-p">{{project.description}}</q-item-section>
          </div>
        </div>
        <div class="row justify-end">
            <q-btn-group push>
              <q-btn target="_blank" icon="mdi-file-document-outline" label="Docs" v-if="project.docs !== null" :href="project.docs"/>
              <q-btn target="_blank" icon="mdi-arrow-right" class="text-white" style="background-color: var(--dark-green);" label="Visit site" v-if="project.siteUrl !== null" :href="project.siteUrl" />
            </q-btn-group>
        </div>
      </q-item>
    </q-list>
  </div>
</template>

<script>
import { ref } from 'vue'

const designs = [
  {
    no: 0,
    name: 'Dotcom Open Recruitment Poster',
    year: 2023,
    url: '/graphic-design/18_dotcomPoster.jpg'
  },
  {
    no: 1,
    name: 'Van Deventeer Maas Indonesia Scholarship Socialization Poster',
    year: 2020,
    url: '/graphic-design/17_vdmi3.jpg'
  },
  {
    no: 2,
    name: 'Poster Task',
    year: 2020,
    url: '/graphic-design/13_neoTugasPoster.jpeg'
  },
  {
    no: 3,
    name: 'Personal Drawing: Girl with beautiful hair holding her Cat',
    year: 2022,
    url: '/graphic-design/11_personalDrawing5.jpg'
  },
  {
    no: 4,
    name: 'Personal Drawing: sillouhette',
    year: 2019,
    url: '/graphic-design/10_personalDrawing4.jpg'
  },
  {
    no: 5,
    name: 'Personal Drawing: My Potrait',
    year: 2020,
    url: '/graphic-design/09_personalDrawing3.jpg'
  },
  {
    no: 6,
    name: 'Personal Drawing: young guy',
    year: 2021,
    url: '/graphic-design/08_personalDrawing2.jpg'
  },
  {
    no: 7,
    name: 'Personal Drawing: no-name',
    year: 2019,
    url: '/graphic-design/07_personalDrawing.jpg'
  },
  {
    no: 8,
    name: 'Personal Drawing: Social Distancing',
    year: 2020,
    url: '/graphic-design/06_socialDistancing.jpg'
  },
  {
    no: 9,
    name: 'Personal Drawing: Poster Contest',
    year: 2020,
    url: '/graphic-design/05_posterContest.jpg'
  }

]

const projects = [
  {
    name: 'Mobile UI for Industrial Engineering Lab Website',
    description: '',
    pictureUrl: '/project/mobile.jpeg',
    docs: 'http://scholar.unand.ac.id/123458/',
    siteUrl: 'https://www.figma.com/proto/6heaGtJ3MTg5YU4N00PX68/PROTOTYPE-MOBILE-EXTERNAL?node-id=41%3A1219&scaling=scale-down&page-id=0%3A1&starting-point-node-id=41%3A1219'
  },
  {
    name: 'Desktop UI for Industrial Engineering Lab Website',
    description: '',
    pictureUrl: '/project/desktop.jpeg',
    docs: 'http://scholar.unand.ac.id/123458/',
    siteUrl: 'https://www.figma.com/proto/ybqvBqnJ5gp4ZpsgrYBiGY/PROTOTYPE-DESKTOP-EXTERNAL?node-id=146%3A77&scaling=scale-down&page-id=0%3A1&starting-point-node-id=146%3A77'
  }
]

export default {
  // name: 'ComponentName',
  setup () {
    return {
      designs,
      slide: ref(0),
      fullscreen: ref(false),
      projects
    }
  }
}
</script>
