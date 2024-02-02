<template>
    <base-card>
        <base-button 
            @click="setSelectedTab('stored-resources')"
            :mode="addResbtn"
            >Stored resources
        </base-button>
        <base-button 
            @click="setSelectedTab('add-resource')"
            :mode="storedResBtn"
            >Add resources
        </base-button>
    </base-card>
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
        AddResource
    },

    computed: {

        addResbtn() {
            return this.selectedTab === 'stored-resources' ? null : 'flat    '
            
        },

        storedResBtn() {
            return this.selectedTab === 'add-resource' ? null : 'flat'
        }
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
            resources: this.storedResources,
            addResource: this.addResource,
            removeResource: this.removeResource
        }
    },

    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },

        addResource(title,description,link) {
            const newResource = {
                id: new Date().toISOString(),
                title: title,
                description: description,
                link: link
            }
            this.storedResources.unshift(newResource);
            this.selectedTab = 'stored-resources';
        },

        removeResource(resId) {
            const resIndex = this.storedResources.findIndex(res => res.id !== resId)
            this.storedResources.splice(resIndex, 1);
        }
    }
}

</script>