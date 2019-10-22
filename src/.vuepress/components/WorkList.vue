<script>
export default {
    name: 'WorkList',
    props: {
        pages: {
            type: Array,
            default: []
        },
        pageSize: {
            type: Number,
            default: 10
        },
        startPage: {
            type: Number,
            default: 0
        }
    },
    data() {
        return {
            currentPage: Math.ceil(this.startPage / this.pageSize),
            selectedTags: [],
        }
    },
    computed: {
        filteredList() {
            if (this.pages) {

                return this.pages.filter(item => {
                    const isWorkPost = !!item.frontmatter.work
                    const isReadyToPublish = new Date(item.frontmatter.date) <= new Date()
                     // check for locales
                    let isCurrentLocale = true;
                    if(this.$site.locales) {
                        const localePath = this.$route.path.split('/')[1] || "";
                        isCurrentLocale = item.relativePath.startsWith(localePath);
                    }
                    // check if tags contain all of the selected tags
                    const hasTags = !!item.frontmatter.tags && this.selectedTags.every((tag) => item.frontmatter.tags.includes(tag))

                    if (!isWorkPost || !isReadyToPublish || (this.selectedTags.length > 0 && !hasTags) || !isCurrentLocale){
                        return false
                    }

                    return true

                }).sort((a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date))
            }
        },
        totalPages() {
            return Math.ceil(this.filteredList.length / this.pageSize)
        },
    },

    mounted() {
        this.currentPage =  Math.min(Math.max(this.currentPage, 0), this.totalPages - 1);
    },

    methods: {
        nextPage() {
            this.currentPage = this.currentPage >= this.totalPages - 1 ? this.totalPages - 1 : this.currentPage + 1
        },
        previousPage() {
            this.currentPage = this.currentPage < 0 ? 0 : this.currentPage - 1
        },
        addTag(tag) {
            const tagExists = this.selectedTags.some(item => {
                return item === tag
            })

            if (!tagExists){
                this.selectedTags = this.selectedTags.concat(tag)
            }
        },
        removeTag(tag) {
            this.selectedTags.filter(t => t != tag)
        },
        removeTag(index){
          this.selectedTags.splice(index, 1);
        },
        resetTags(){
            this.selectedTags = []
        }
    }
}
</script>

<template>
	<div>
        <div
            v-if="selectedTags.length > 0"
            class="filtered-heading"
        >
            <h2>Filters</h2>
            <button
                type="button"
                @click="resetTags"
                class="btn clear-filter-btn"
            >
                Clear filter
            </button>
            <ul class="filter-list">
              <li class="filter-list__item" v-for="(selectedTag, index) in selectedTags">{{ selectedTag }} <button class="filter-list__item-button" type="button" @click="removeTag(index)">✕</button></li>
            </ul>
        </div>
        <ul class="work-list">
            <li v-for="(item, index) in filteredList"
                class="work-list__item">
                <WorkPreview
                    v-show="index >= currentPage * pageSize && index < (currentPage + 1) * pageSize"
                    :item="item"
                />
                <ul class="work-list__tags">
                    <li class="work-list__tag-item" v-for="tag in item.frontmatter.tags">
                        <button class="work-list__tag-button" @click="addTag(tag)">{{ tag }}</button>
                    </li>
                </ul>
            </li>
        </ul>

        <div class="pagination">
            <button v-show="currentPage > 0"
                @click="previousPage"
                class="button--pagination"
                type="button"
            >
                Previous
            </button>
            <button v-show="currentPage < totalPages - 1"
                @click="nextPage"
                class="button--pagination"
                type="button"
            >
                Next
            </button>
        </div>
    </div>
</template>

<style scoped lang="scss">
.work-list {
	padding: 0;
	margin: 0;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-column-gap: 20px;
    grid-row-gap: 20px;
}

.work-list__item {
  list-style: none;
}

.filter-list {
  list-style: none;
  display: flex;
  align-items: flex-end;
  padding-left: 0;
  .filter-list__item {
    color: #fff;
    padding: 0 2.5em 0 1em;
    border-radius: 27px;
    background: #084C61;
    position: relative;
    margin-right: 1em;    
    .filter-list__item-button {
      position: absolute;
      color: #084C61;
      background: #fff;
      border-radius: 100%;
      -webkit-appearance: none;
      border: 0;
      width: 20px;
      height: 20px;
      font-size: 10px;
      right: 3.5px;
      top: 3.5px;
      cursor: pointer;
    }
  }
}

.work-list__tags {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  padding: 0;
  .work-list__tag-item {
    margin: 0 .5em;
  }
  .work-list__tag-button {
    padding-bottom: 5px;
    -webkit-style: none;
    color: #121619;
    padding: .5em;
    border-radius: 0 4px 4px 0;
    border: 0;
    background: rgba(255, 232, 194, 0.3);
    font-size: 11px;
    padding: .3em .5em;
    cursor: pointer;
    position: relative;
    &:before {
    	content:"";
    	float:left;
    	position:absolute;
    	top:0;
    	left:-10px;
    	width:0;
    	height:0;
    	border-color:transparent rgba(255, 232, 194, 0.3) transparent transparent;
    	border-style:solid;
    	border-width:10px 10px 10px 0;
    	}
  }
}

.blog-list__tags {
    margin-bottom: 15px;
}

.button--pagination {
	background-color: #32c8cf;
	border-radius: 4px;
	color: #fff;
	font-size: 0.8rem;
	padding: 0.5rem 0.75rem;
	text-transform: uppercase;
	font-weight: 700;
	box-shadow: 0 0;
	transition: background-color 0.2s ease-in, color 0.2s ease-in;
}

.button--pagination:hover {
    background-color: #fff;
    border: 1px solid #32c8cf;
    border-radius: 4px;
    color: #32c8cf;
}

.clear-filter-btn {
    align-self: center;
    margin-left: 20px;
}

.filtered-heading {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

.pagination {
    text-align: center;
}
</style>
