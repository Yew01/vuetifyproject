<template>
  <v-app>
    <v-main>
      <v-container class="fill-height">
        <v-responsive class="mx-auto">
          <v-form fast-fail @submit.prevent class="pa-4">
            <v-card  class="mx-auto pa-2 border-lg mt-5" width="auto">
              <v-card-title class="text-center">
                Registration Page
              </v-card-title>
              <v-card-subtitle class="text-center">
                asdasdadaad
              </v-card-subtitle>

              <br>
              <v-row>
                <v-col cols="4">
                  <v-row>
                    <v-col cols="12" class="text-center">
                      <v-icon size="200" v-if="imageUrl" :src="imageUrl">mdi mdi-account-circle</v-icon>
                      <v-icon size="200" v-else>mdi mdi-account-circle</v-icon>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="12" class="text-center">
                      <v-btn height="40" width="200" @click="uploadFile">
                        <v-file-input v-model="file" accept=".jpg, .jpeg, .png" hide-input></v-file-input>
                        <div class="text-h6 d-flex">Upload</div>   
                        </v-btn>
                    </v-col>
                    <v-col cols="12" class="text-center">
                      <v-btn height="40" width="100">
                        <v-icon left size="30">mdi-cancel</v-icon>
                        Upload
                        </v-btn>
                    </v-col>
                  </v-row>
                </v-col>
                <v-col cols="8">
                  <v-row>
                    <v-col cols="6">
                      <v-text-field
                        label="firtsname"
                        prepend-inner-icon="mdi-account">
                      </v-text-field>            
                    </v-col>
                    <v-col cols="6">
                      <v-text-field
                      label="last name"
                      prepend-inner-icon="mdi-account">
                      </v-text-field>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="4">
                      <div>Gender</div>
                      <div class="d-flex flex-wrap">
                      <v-checkbox label="Male" v-model="gender" value="male"></v-checkbox>
                      <v-checkbox label="Female" v-model="gender" value="female"></v-checkbox>
                      </div>
                    </v-col>
                    <v-col cols="8">
                      <v-text-field
                        label="BOD"
                        prepend-inner-icon="mdi-calendar-account-outline"
                        type="date"></v-text-field>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="12">
                      <div class="text-left text-h5 pa-auto">Address</div>
                      <v-text-field
                        label="Stree Address"
                        prepend-inner-icon="mdi-map-marker"></v-text-field>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="3">
                      <v-text-field
                        label="City"
                        prepend-inner-icon="mdi-map-marker"></v-text-field>
                    </v-col>
                    <v-col cols="3">
                      <v-text-field
                        label="State"
                        prepend-inner-icon="mdi-map-marker"></v-text-field>
                    </v-col>
                    <v-col cols="3">
                      <v-text-field
                        label="Country"
                        prepend-inner-icon="mdi-map-marker"></v-text-field>
                    </v-col>
                    <v-col cols="3">
                      <v-text-field
                        label="Zip Code"
                        prepend-inner-icon="mdi-map-marker"></v-text-field>
                    </v-col>
                  </v-row>
                  
                  <v-row>
                    <v-col cols="6">
                      <div>Email
                      <v-text-field
              label="Email"
              prepend-inner-icon="mdi-email"
              type="email"></v-text-field>
              </div>
                    </v-col>
                    <v-col cols="6">
                      <div>Contact
                      <v-text-field
              label="Phone"
              prepend-inner-icon="mdi-cellphone"></v-text-field>
                      </div>
                    </v-col>
                  </v-row>  
                </v-col>
              </v-row>
            </v-card>
          </v-form>
        </v-responsive>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
  data() {
    return {
      gender: null,
      file: null,
      imageUrl: null
    };
  },
  methods:{
    uploadFile() {
      const formData = new FormData();
      formData.append('image', this.file);

      // Replace with your actual server endpoint
      const url = 'https://your-server-endpoint';

      fetch(url, {
        method: 'POST',
        body: formData
      })
        .then(response => response.json())
        .then(data => {
          if (data.success) {
            this.imageUrl = data.imageUrl;
          } else {
            console.error('Error uploading image:', data.message);
          }
        })
        .catch(error => {
          console.error('Error uploading image:', error);
        });
    },

    cancelUpload() {
      this.file = null;
      this.imageUrl = null;
    }
  }
};
</script>
