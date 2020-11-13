<template>
    <div class="flex flex-row justify-items-center layout">
        <div class=" flex-col flex pr-12  items-center justify-center max-w-xs">

            <img src='~assets/index.png'  class='rounded-full h-32 w-32'>
            <div class="flex-row">
                <p class = 'my-2 text-center'>{{about.name}} </p>
                <p class="my-2 text-center"> {{about.organization}}</p>
                 </div>
            <div class="flex flex-row items-center ">
                <a :href="about.email" class='link-email mx-1'></a>
                <a :href="`https://www.twitter.com/` + about.twitter" class='mx-1 link-twitter'></a>
                <a :href="`https://www.github.com/` + about.github" class='link-github mx-1'></a>
                <a :href="`https://www.linkedin.com/in/` + about.linkedin" class='link-linkedin mx-1'></a>
            </div>
        </div>
        
        <div class="mr-8 max-w-xs">
            <div class="description-paragraph">{{about.description}}</div>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        about: {
            type: Object,
            required: true
        }
    }
}
</script>

<style >
.link-twitter {
  background-image: url('~assets/svg/iconfinder_twitter_317720.svg');
  display: inline-block;
  width: 40px;
  height: 40px;
  background-size: 40px 40px;
}
.link-github {
  background-image: url('~assets/svg/iconfinder_github_317712.svg');
  display: inline-block;
  width: 40px;
  height: 40px;
  background-size: 40px 40px;
}
.link-linkedin {
  background-image: url('~assets/svg/iconfinder_social_media_applications_14-linkedin_4102586.svg');
  display: inline-block;
  width: 40px;
  height: 40px;
  background-size: 40px 40px;
}
.link-email {
  background-image: url('~assets/svg/iconfinder_mail_115714.svg');
  display: inline-block;
  width: 40px;
  height: 40px;
  background-size: 40px 40px;
}
</style>