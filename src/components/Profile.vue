<template>
  <div>
    <div class="row">
      <div class="col-md-4">
        <div class="card" style="width: 18rem;">
          <img class="card-img-top" :src="user.avatar_url" alt="Card image cap">
          <ul class="list-group list-group-flush">
            <li class="list-group-item font-weight-bold"><i class="fas fa-folder text-secondary"></i> Repositórios: <span class="badge float-right">{{user.public_repos}}</span>
            </li>
            <li class="list-group-item font-weight-bold"><i class="fas fa-users text-secondary"></i> Seguidores: <span class="badge float-right">{{user.followers}}</span>
            </li>
            <li class="list-group-item font-weight-bold"><i class="fas fa-user-friends text-secondary"></i> Seguindo: <span class="badge float-right">{{user.following}}</span>
            </li>
          </ul>
          <div class="card-body">
            <a :href="user.html_url" target="_blank" class="btn btn-success btn-block">Ver Perfil</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["user"]
};
</script>