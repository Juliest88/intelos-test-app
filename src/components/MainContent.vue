<template>
  <div class="main-content">
    <div class="top-header">
      <SearchBar class="search-bar" />
      <div class="top-actions-buttons">
        <IconDarkMode />
        <div class="user-profile">
          <IconAccountCircle />
          <span class="profile-name">OM</span>
        </div>
        <div class="notification-wrapper">
          <IconNotification />
          <n-tag
            class="notification-count-tag"
            round
            size="small"
            :color="{ color: '#2E5BFF', borderColor: '#2E5BFF', textColor: '#FFFFFF' }"
          >
            15+
          </n-tag>
        </div>
        <n-divider vertical class="vertical-divider" />
        <n-button color="#2C2E30" style="border-radius: 5px">Create new</n-button>
      </div>
    </div>
    <CountriesTableContainer @onSelectedCountry="openMap" />
    <n-modal
      preset="card"
      v-model:show="showModal"
      style="width: 80%; height: 80%"
      @on-after-leave="closeMap"
    >
      <template #header>
        <h3>Country Location</h3>
      </template>
      <template #default>
        <MapComponent :markerLatLng="countryCoordinates" />
      </template>
    </n-modal>
  </div>
</template>

<script>
import CountriesTableContainer from './CountriesTableContainer.vue'
import IconAccountCircle from './icons/IconAccountCircle.vue'
import IconDarkMode from './icons/IconDarkMode.vue'
import IconNotification from './icons/IconNotification.vue'
import MapComponent from './MapComponent.vue'
import SearchBar from './SearchBar.vue'
import { NDivider, NModal, NTag } from 'naive-ui'

export default {
  components: {
    SearchBar,
    CountriesTableContainer,
    MapComponent,
    NModal,
    IconDarkMode,
    IconAccountCircle,
    IconNotification,
    NTag,
    NDivider,
  },
  data() {
    return {
      showModal: false,
      countryCoordinates: null,
    }
  },
  methods: {
    openMap(country) {
      if (country && country.latlng) {
        this.countryCoordinates = country.latlng
        this.showModal = true
      } else {
        console.error('Invalid coordinates:', country)
      }
    },
    closeMap() {
      this.showModal = false
    },
  },
}
</script>

<style scoped>
.main-content {
  .top-header {
    display: flex;
    width: 100%;
    margin-bottom: 25px;
    .search-bar {
      width: 332px;
      height: 36px;
      margin-right: auto;
    }

    .top-actions-buttons {
      display: flex;
      align-items: center;

      .vertical-divider {
        width: 1px;
        height: 28px;
        background-color: #d1d5db;
      }

      & > * {
        margin-right: 30px;

        &:hover {
          cursor: pointer;
        }
      }

      .user-profile {
        display: flex;

        .profile-name {
          margin-left: 10px;
        }
      }

      .notification-wrapper {
        position: relative;

        .notification-count-tag {
          position: absolute;
          bottom: calc(100% - 4px);
          left: calc(100% - 4px);
          height: 16px;
          font-size: 10px;

          &:hover {
            cursor: pointer;
          }
        }
      }
    }
  }
}
</style>
