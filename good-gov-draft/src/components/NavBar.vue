<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">GoodGovDraft</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item pe-1">
            <button type="button" @click="goToHome()" class="btn btn-light">
                <a class="nav-link active" aria-current="page">Home</a>
            </button>
        </li>
        <li class="nav-item pe-1">
            <button type="button" @click="goToCandidates()" class="btn btn-light">
                <a class="nav-link">Candidates</a>
            </button>
        </li>
        <li class="nav-item pe-1">
            <button type="button" @click="goToConventions()" class="btn btn-light">
                <a class="nav-link">Conventions</a>
            </button>
        </li>
        <li class="nav-item pe-1">
            <button type="button" @click="goToAbout()" class="btn btn-light">
                <a class="nav-link">About</a>
            </button>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>

<script>
export default {
  name: 'NavBar',
  methods: {
    goToHome() {
      this.$router.push('/');
    },
    goToAbout() {
      this.$router.push('/About');
    },
    goToCandidates() {
      this.$router.push('/Candidates');
    },
    goToConventions() {
      this.$router.push('/Conventions');
    },
  }
}
</script>