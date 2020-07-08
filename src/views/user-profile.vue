<template>
  <section class="profile">
    <div v-if="user" class="profile-container">
      <img class="profile-image" :src="user.userImgUrl" alt />
      <!-- <avatar size="80px" :url="avatarUrl(user.userImgUrl)" /> -->
      <div class="profile-container-intro">
        <h2>{{user.firstName}} {{user.lastName}}</h2>
        <div>Member since {{user.createdAt | date}}</div>
        <p>{{user.bio}}</p>
        <div>
          {{user.firstName}}'s rating:
          <rating show-only :total="user.rating" />
        </div>
      </div>
    </div>
    <div>
      <bookings />
    </div>
  </section>
</template>

<script>
import rating from "@/cmps/rate.vue";
import bookings from "@/views/bookings.vue";

export default {
  components: {
    rating,
    bookings
  },
  data() {
    return {
      bookings: [],
      user: null
    };
  },
  computed: {
    userBookings() {
      return this.$store.getters.userBookings;
    }
  },
  methods: {
    // async getBookings() {
    //   const bookingByUserId = this.user;
    //   this.bookings = await this.$store.dispatch({
    //     type: "loadUserBookings",
    //     bookingByUserId
    //   });
    // }
    async getUser() {
      const userId = this.$route.params.id;
      var user = null;
      if (!userId) {
        user = this.$store.getters.user;
      } else {
        user = await this.$store.dispatch({
          type: "loadUserProfile",
          userId
        });
      }
      this.user = user;
    }
  },
  created() {
    this.getUser();
  }
  // this.getBookings();
};
</script>

<style>
/* .profile-container {
  display: flex;
  justify-content: space-between;
} */
/* .profile-container-intro {
  display: flex;
  flex-direction: column;
  margin-left: 10px;
} */
/* .profile-image {
  height: 180px;
} */
/* .profile {
  display: flex;
  flex-direction: column;
} */
</style>
