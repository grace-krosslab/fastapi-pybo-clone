<script>
  import { link } from "svelte-spa-router";
  import { page, access_token, username, is_login } from "../lib/store";
</script>

<!-- 네비게이션바 -->
<nav class="navbar navbar-expand-lg navbar-light bg-light border-bottom">
  <div class="container-fluid">
    <a
      use:link
      href="/"
      class="navbar-brand"
      on:click={() => {
        $page = 0;
      }}>Pybo</a
    >
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon" />
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        {#if $is_login}
          <li class="nav-item">
            <a
              use:link
              href="/user-login"
              class="nav-link"
              on:click={() => {
                $access_token = "";
                $username = "";
                $is_login = false;
              }}>로그아웃 ({$username})</a
            >
          </li>
        {:else}
          <li class="nav-item">
            <a use:link href="/user-create" class="nav-link">회원가입</a>
          </li>
          <li class="nav-item">
            <a use:link href="/user-login" class="nav-link">로그인</a>
          </li>
        {/if}
      </ul>
    </div>
  </div>
</nav>
