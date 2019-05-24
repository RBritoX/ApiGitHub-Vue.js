<template>
  <div class="card card-body mb-2">
    <div class="row">
      <div class="col-md-6">
        <a :href="repo.html_url" class="font-weight-bold" target="_blank" >{{repo.name}}</a>
      </div>
      <div class="col-md-6">
        <span class="badge"><i class="fas fa-star text-warning"></i> Stars: {{repo.stargazers_count}}</span>
        <span class="badge"><i class="fas fa-eye text-primary"></i> Watch: {{ repo.watchers_count}}</span>
        <span class="badge"><i class="fas fa-code-branch text-success"></i> Forks: {{ repo.forks_count }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["repo"]
};
</script>