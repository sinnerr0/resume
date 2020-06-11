<template>
  <v-app>
    <v-main>
      <v-card class="ma-5" elevation="5" shaped>
        <v-card-text>
          <v-container fluid>
            <v-row class="align-center">
              <v-col class="d-flex-column">
                <div class="text-h3 text-uppercase blue--text font-weight-bold">
                  {{ name }}
                </div>
                <div class="text-h5">{{ position }}</div>
              </v-col>
              <v-col class="d-flex">
                <v-spacer></v-spacer>
                <v-avatar size="100">
                  <v-img src="profile.jpg"></v-img>
                </v-avatar>
              </v-col>
              <v-col style="border-left: 1px solid rgba(0, 0, 0, 0.08);">
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-cellphone</v-icon>
                  <v-btn text :href="`tel:${tel}`">{{ tel }}</v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-email</v-icon>
                  <v-btn text class="text-none" :href="`mailto:${email}`">{{
                    email
                  }}</v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-linkedin</v-icon>
                  <v-btn text :href="linkedin">www.linkedin.com</v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-github</v-icon>
                  <v-btn text :href="github">github.com</v-btn>
                </div>
              </v-col>
            </v-row>
            <v-row
              class="my-5"
              style="border-top: 1px solid rgba(0, 0, 0, 0.08);"
            >
              <v-col> </v-col>
            </v-row>
            <v-row>
              <v-hover v-slot:default="{ hover }">
                <v-card
                  outline
                  :elevation="hover ? 2 : 0"
                  width="100%"
                  class="ma-3"
                >
                  <v-card-title>
                    WORK EXPERIENCE
                  </v-card-title>
                  <v-card-text> </v-card-text>
                </v-card>
              </v-hover>
              <v-hover v-slot:default="{ hover }">
                <v-card
                  outline
                  :elevation="hover ? 2 : 0"
                  width="100%"
                  class="ma-3"
                >
                  <v-card-title>
                    PROJECTS
                  </v-card-title>
                  <v-card-text> </v-card-text>
                </v-card>
              </v-hover>
              <v-hover v-slot:default="{ hover }">
                <v-card
                  outline
                  :elevation="hover ? 2 : 0"
                  width="100%"
                  class="ma-3"
                >
                  <v-card-title>
                    INFORMATION
                  </v-card-title>
                  <v-card-text> </v-card-text>
                </v-card>
              </v-hover>
              <v-hover v-slot:default="{ hover }">
                <v-card
                  outline
                  :elevation="hover ? 2 : 0"
                  width="100%"
                  class="ma-3"
                >
                  <v-card-title>
                    EDUCATION
                  </v-card-title>
                  <v-card-text> </v-card-text>
                </v-card>
              </v-hover>
              <v-hover v-slot:default="{ hover }">
                <v-card
                  outline
                  :elevation="hover ? 2 : 0"
                  width="100%"
                  class="ma-3"
                >
                  <v-card-title>
                    AWARDS
                  </v-card-title>
                  <v-card-text> </v-card-text>
                </v-card>
              </v-hover>
            </v-row>
            <v-row> </v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-main>

    <v-footer app elevation="1">
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().toLocaleDateString() }}</div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  head() {
    return {
      title: '[Resume] Kyongsik.C',
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      ],
      link: [{ rel: 'favicon', href: 'favicon.ico' }],
    }
  },

  data() {
    return {
      name: 'Kyongsik Choi',
      position: 'Senior Software Engineer',
      tel: '010-9261-1248',
      email: 'sinnerr0@gmail.com',
      linkedin:
        'http://www.linkedin.com/in/%EA%B2%BD%EC%8B%9D-%EC%B5%9C-bb108871',
      github: 'https://github.com/sinnerr0',
    }
  },
}
</script>
