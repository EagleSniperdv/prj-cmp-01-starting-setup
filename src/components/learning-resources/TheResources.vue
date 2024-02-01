<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')">Stored resources</base-button>
        <base-button @click="setSelectedTab('add-resource')">Add resources</base-button>
    </base-card>
    <component :is="selectedTab"></component>
</template>

<script>

import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {

    components: {

        StoredResources,
        AddResource
    },

    data() {
        return {
            selectedTab: 'stored-resources',

            storedResources: [
                        {
                            id: "material1",
                            title: "Vue official site",
                            description: "this is the description",
                            link: "www.vue.org"
                        },

                        {
                            id: "material2",
                            title: "Google official site",
                            description: "this is the description for google",
                            link: "www.google.com"
                        },
                    ]
        }
    },

    provide() {
        return {
            resources: this.storedResources
        }
    },

    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        }
    }
}

</script>