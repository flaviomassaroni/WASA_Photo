<script>
export default {
	data: function() {
		return {
			errormsg: null,
			loading: false,
			loggingUsername: "",
			logged: {},
		};
	},
	methods: {
		async login() {
			this.loading = true;
			this.errormsg = null;

			try {
				let response = await this.$axios.post(`/session?username=${this.loggingUsername}`);
				
				sessionStorage.setItem("userid", response.data.UserID);
				sessionStorage.setItem("username", response.data.Username);
				sessionStorage.setItem("logged", true);

				this.$router.replace("/stream", {
					headers: {
						Authorization: sessionStorage.getItem("userid"),
					},
				});
			} catch (e) {
				this.errormsg = e.toString();
			}
			this.loading = false;
		},
	},
};
</script>


<template>
	<div class="login-container">
		<div class="header">
			<h1 class="h2">Login</h1>
		</div>

		<ErrorMsg v-if="errormsg" :msg="errormsg"></ErrorMsg>

		<form @submit.prevent="login" class="login-form">
			<div class="form-group">
				<label for="username">Username:</label>
				<input 
					id="username" 
					type="text" 
					v-model="loggingUsername" 
					class="form-control" 
					placeholder="Enter your username" 
					required 
				/>
			</div>
			<button class="btn btn-primary" type="submit" :disabled="loading">
				<span v-if="loading" class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span>
				<span v-if="!loading">Login</span>
			</button>
		</form>
	</div>
</template>


<style scoped>
.login-container {
	max-width: 400px;
	margin: 50px auto;
	padding: 20px;
	border-radius: 8px;
	box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
	background-color: #f8f9fa;

}

.header {
	text-align: center;
	margin-bottom: 20px;
}

.form-group {
	margin-bottom: 15px;
}

.form-control {
	width: 100%;
	padding: 10px;
	border: 1px solid #ced4da;
	border-radius: 4px;
	font-size: 16px;
}

.btn-primary {
	width: 100%;
	padding: 10px;
	font-size: 18px;
	font-weight: bold;
	background-color: #cccccc;
	border: none;
	border-radius: 4px;
	color: white;
	cursor: pointer;
	transition: background-color 0.3s;
}

.btn-primary:hover {
	background-color: #000000;
}

.spinner-border {
	margin-right: 8px;
}

</style>

