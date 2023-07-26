<template>
<div class="container">
    <form @submit.prevent="submitForm">
        <div class="field">
            <label class="label">İsim</label>
            <div class="control">
              <input v-model="post.firstname" class="input" type="text" placeholder="İsim">
            </div>
          </div>

          <div class="container">
            <div class="field">
                <label class="label">Soyisim</label>
                <div class="control">
                  <input v-model="post.lastname" class="input" type="text" placeholder="Soyisim">
                </div>
              </div>
          
          <div class="field">
            <label class="label">Şifre</label>
            <div class="control has-icons-left has-icons-right">
              <input v-model="post.password" class="input is-success" type="text" placeholder="Şifre">
              <span class="icon is-small is-left">
                <i class="fas fa-user"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-check"></i>
              </span>
            </div>
          </div>
          
          <div class="field">
            <label class="label">Email</label>
            <div class="control has-icons-left has-icons-right">
              <input v-model="post.email" class="input is-danger" type="email" placeholder="Email">
              <span class="icon is-small is-left">
                <i class="fas fa-envelope"></i>
              </span>
              <span class="icon is-small is-right">
                <i class="fas fa-exclamation-triangle"></i>
              </span>
            </div>
            <p class="help is-danger">Bu mail geçersiz</p>
          </div>
          
    
          <div class="field is-grouped">
            <div class="control">
              <button type="submit" class="button is-primary">Onayla</button>
            </div>

          </div> 
    </div>
    </form>

</div>
</template>

<script>
export default{
    props: ["post", "submitForm"],
}
</script>

<style>

</style>