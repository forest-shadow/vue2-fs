<template>
  <article :id="post.id" class="media" :class="{ 'blue-border': post.votes >= 20 }">
    <figure class="media-left">
      <img class="image is-64x64" :src="getImageSrc(post.submissionImage, 'submissions')">
    </figure>
    <div class="media-content">
      <div class="content">
        <p>
          <strong>
            <a href="#" class="has-text-info">{{ post.title }}</a>
            <span class="tag is-small">{{ `#${post.id}` }}</span>
          </strong>
          <br>
          {{ post.description }}
          <br>
          <small class="is-size-7">
            Submitted by:
            <img class="image is-24x24"
                 :src="getImageSrc(post.avatar, 'avatars')">
          </small>
        </p>
      </div>
    </div>
    <div class="media-right" @click="$emit('upvote', post.id)">
        <span class="icon is-small">
          <i class="fa fa-chevron-up"></i>
          <strong class="has-text-info">{{ post.votes }}</strong>
        </span>
    </div>
  </article>
</template>

<script>
export default {
  name: 'Post',
  props: ['post'],
  methods: {
    getImageSrc(imageName, imageDir) {
      let context;
      switch (imageDir){
        case 'submissions':
          context = require.context('../assets/submissions', true, /\.(?:jpg|png)$/);
          break;
        case 'avatars':
          context = require.context('../assets/avatars', true, /\.(?:jpg|png)$/);
          break;
      }

      let imageNameBits = imageName.split(/(\\|\/)/g).pop().split('.');

      return context('./' + imageNameBits[0] + `.${imageNameBits[1]}`)
    }
  }
}
</script>