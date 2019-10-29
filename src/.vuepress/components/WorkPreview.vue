<script>
    export default {
        name: 'WorkPreview',
        props: {
            item: {
                type: Object,
                required: true
            }
        },
        computed: {
            formatPublishDate() {
                const dateFormat = new Date(this.item.frontmatter.date)
                const options = {
                    year: 'numeric',
                    month: 'long',
                    day: 'numeric'
                }

                return dateFormat.toLocaleDateString('en-US', options)
            }
        }
    }
</script>

<template>
    <section>
        <router-link class="work-post__image-container" :to="item.path">
            <img class="work-post__image" :src="item.frontmatter.preview ? item.frontmatter.preview : '/default.jpg'">
        </router-link>
        <h3 class="blog-post__title">{{ item.frontmatter.title }}</h3>
        <p v-if="item.frontmatter.excerpt">{{ item.frontmatter.excerpt }}</p>
    </section>
</template>

<style scoped lang="scss">
    .work-post__image-container {
      background-color: #eaecef;
      display: block;
      transition: all ease 0.6s;
      line-height: 0;
      .work-post__image {
        transition: all ease 0.3s;
      }
      &:hover .work-post__image {
        transform: scale(1.125);
      }
    }
    .blog-post__button {
        margin-bottom: 1.5rem;
        display: inline-block;
    }

    .blog-post__title {
        margin-top: 0.5rem;
    }

    .work-post__image-container

    .work-post__image {
        max-width: 100%;
    }

    .button {
        border: 1px solid #084C61;
        border-radius: 4px;
        color: #084C61;
        font-size: 0.8rem;
        padding: 0.5rem 0.75rem;
        text-transform: uppercase;
        font-weight: 700;
        box-shadow: 0 0;
        transition: background-color 0.2s ease-in, color 0.2s ease-in;
    }

    .tag-list {
        list-style: none;
        padding-left: 0;
        display: flex;
        margin-bottom: 25px;
    }

    .tag-list__item {
        margin-left: 10px;
    }

    .tag-list__item:first-child {
        margin-left: 0;
    }

    .tag-list__btn {
        padding: 5px;
        font-size: 0.9rem;
        background-color: #fff;
    }
</style>
