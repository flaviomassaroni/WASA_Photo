<script>
import { RouterLink, RouterView } from 'vue-router'

export default {

	data: function() {
		return {
			logged: false,
		}
	},

	methods: {
		toggleLogged() {
			this.logged = true;
		},
	}
}
</script>

<template>

	<header class="navbar navbar-dark sticky-top bg-dark flex-md-nowrap p-0 shadow">
		<a class="navbar-brand col-md-3 col-lg-2 me-0 px-3 fs-6" href="#/">WASAPhoto</a>
		<button class="navbar-toggler position-absolute d-md-none collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#sidebarMenu" aria-controls="sidebarMenu" aria-expanded="false" aria-label="Toggle navigation">
			<span class="navbar-toggler-icon"></span>
		</button>
	</header>

	<div class="container-fluid">
		<div class="row">
				<nav id="sidebarMenu" class="col-md-3 col-lg-2 d-md-block bg-light sidebar collapse">
					<div class="position-sticky pt-3 sidebar-sticky">
						<h6 class="sidebar-heading d-flex justify-content-between align-items-center px-3 mt-4 mb-1 text-muted text-uppercase">
							<span>General</span>
						</h6>
						<ul class="nav flex-column">
							<li class="nav-item">
								<RouterLink to="/stream" class="nav-link">
									<svg class="feather"><use href="/feather-sprite-v4.29.0.svg#home"/></svg>
									Home
								</RouterLink>
							</li>
							<li class="nav-item">
								<RouterLink to="/profile" class="nav-link">
									<svg class="feather"><use href="/feather-sprite-v4.29.0.svg#user"/></svg>
									Profile
								</RouterLink>
							</li>
							<li class="nav-item">
								<RouterLink to="/session" class="nav-link">
									<svg class="feather"><use href="/feather-sprite-v4.29.0.svg#key"/></svg>
									Login
								</RouterLink>
							</li>
						</ul>
					</div>
				</nav>
			<main class="col-md-9 ms-sm-auto col-lg-10 px-md-4">
				<RouterView />
			</main>
		</div>
		
	</div>
</template>

<style>
.sidebar {
	position: fixed;
	top: 0;
	bottom: 0;
	left: 0;
	z-index: 100;
	box-shadow: inset -1px 0 0 rgba(0, 0, 0, .1);
	background: linear-gradient(to bottom, #ffffff, #cccccc);
}
	
</style>
