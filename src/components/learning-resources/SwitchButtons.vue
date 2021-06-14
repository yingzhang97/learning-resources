<template>
  <the-card>
    <the-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
    >Stored Resources</the-button>
    <the-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resource</the-button>
  </the-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'Github',
          title: 'Github',
          description: 'a programming community used for code sharing and facilitate project management',
          link: 'https://github.com/',
        },
        {
          id: 'stackoverflow',
          title: 'Stack Overflow',
          description: 'a question and answer website for professional and enthusiast programmers',
          link: 'https://stackoverflow.com/',
        },
        {
          id: 'geeksforgeeks',
          title: 'GeeksforGeeks',
          description: 'a computer science portal for geeks',
          link: 'https://www.geeksforgeeks.org/',
        },
        {
          id: 'W3school',
          title: 'W3school',
          description: 'a school for web developers, covering all the aspects of web development',
          link: 'https://www.w3schools.com/',
        },
        {
          id: 'Wikipedia',
          title: 'Wikipedia',
          description: 'an online free encyclopedia',
          link: 'https://en.wikipedia.org/wiki/Main_Page',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId) {
      const resIndex = this.storedResources.findIndex(res => res.id === resId);
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>