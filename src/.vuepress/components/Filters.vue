<script>
export default {
    name: 'Filters',
    data() {
        return {
            currentPage: Math.ceil(this.startPage / this.pageSize),
            selectedTags: [],
        }
    },

    methods: {
        addTag(tag) {
            const tagExists = this.selectedTags.some(item => {
                return item === tag
            })

            if (!tagExists){
                this.selectedTags = this.selectedTags.concat(tag)
            }
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
            <ul class="filter-list">
              <li class="filter-list__item" v-for="(selectedTag, index) in selectedTags">{{ selectedTag }} <button class="filter-list__item-button" type="button" @click="removeTag(index)">✕</button></li>
              <li class="filter-list__item filter-list__item--all-filters">
                Clear filters
                <button
                  type="button"
                  @click="resetTags"
                  class="btn filter-list__item-button"
              >✕</button>
              </li>
            </ul>
        </div>
    </div>
</template>

<style scoped lang="scss">

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
      transition: all 0.3s ease;
      &:hover {
        font-size: 11px;
        font-weight: bold;
      }
    }
  }
  .filter-list__item--all-filters {
    background: rgba(255, 232, 194, 1);
    color: #121619;
  }
}
</style>
