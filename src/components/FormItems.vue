<script>
export default {
	name: "FormItems",
	data() {
		return {
			inputFields: {}
		};
	},
	render(createElement) {
		var self = this;
		return createElement(
			"div",
			{
				class: {
					main: true
				}
			},
			[
				createElement(
					"div",
					{
						class: {
							"form-item": true
						}
					},
					[
						createElement("div", {}, [
							createElement(
								"h4",
								{},
								"New To do"
							)
						]),
						createElement("div", {}, [
							createElement("input", {
								props: {
									value:
										self.value
								},
								attrs: {
									type:
										"text",
									placeHolder:
										"Type the description of your new to do"
								},
								on: {
									input: function(
										event
									) {
										self.inputFields[
											"description"
										] =
											event.target.value;
									}
								}
							})
						]),
						createElement("div", {}, [
							createElement(
								"p",
								{},
								"Deadline to do:"
							),
							createElement("input", {
								props: {
									value:
										self.value
								},
								attrs: {
									type:
										"date"
								},
								on: {
									input: function(
										event
									) {
										self.inputFields[
											"deadline"
										] =
											event.target.value;
									}
								}
							})
						]),
						createElement("div", {}, [
							createElement("input", {
								attrs: {
									value:
										"New Todo",
									type:
										"Submit"
								},
								on: {
									click: function() {
										self.inputFields[
											"newtodo"
										] = true;
										self.$emit(
											"newTodo",
											self.inputFields
										);
									}
								}
							})
						])
					]
				)
			]
		);
	}
};
</script>

<style>
*,
body,
html {
	margin: 0 0;
	padding: 0 0;
	box-sizing: border-box;
}
.main {
	width: 100vw;
	height: 48vh;
	display: flex;
	flex: 1;
	justify-content: center;
	align-items: center;
}
.form-item {
	border: none;
	margin: 0.2rem;
	background: rgba(0, 155, 59, 0.933);
	width: 50vw;
	height: 40vh;
	max-width: 500px;
	max-height: 200px;
	border-radius: 1rem;
	display: grid;
	grid-template-rows: 1fr 1fr 1fr 1fr;
	grid-template-columns: 1fr;
}
.form-item div {
	margin-top: 0.3rem;
	flex: 1;
	display: flex;
}
.form-item div:first-child {
	margin-top: 0.4rem;
	justify-content: center;
	align-items: center;
	font-size: 1.2rem;
}
.form-item div:nth-child(2) {
	justify-content: center;
}
.form-item div:nth-child(2) > input {
	margin-top: 0.1rem;
	width: 26vw;
	background: rgb(0, 0, 0);
	border: none;
	color: white;
	height: 6vh;
	font-size: 1rem;
	border-radius: 0.6rem;
}
.form-item div:nth-child(2) > input:focus {
	border: 2px solid rgb(147, 255, 195);
}
.form-item div:nth-child(2) > input:focus::placeholder {
	color: black;
}
.form-item div:nth-child(3) {
	flex-direction: column;
	align-items: center;
}
.form-item div:nth-child(3) > input {
	width: 30vw;
	margin: 0.4rem 0rem;
	border: none;
	color: white;
	font-size: 1rem;
	padding: 0.2rem;
	border-radius: 0.6rem;
	background: black;
}
.form-item div:nth-child(3) > input:focus {
	border: 2px solid rgb(147, 255, 195);
}
.form-item div:nth-child(4) {
	justify-content: center;
	align-items: center;
}
.form-item div:nth-child(4) input {
	color: #ffffff;
	background: black;
	border-radius: 0.5rem;
	font-size: 1rem;
	border: none;
	border-radius: 0.5rem;
	padding: 0.1rem 0.4rem;
}
.form-item div:nth-child(4) > input:active {
	border: 5px solid rgb(255, 255, 255);
}
@media (min-width: 320px) {
	.form-item {
		width: 80vw;
		height: 30vh;
	}
	.form-item div {
		margin-top: 0.1rem;
	}
	.form-item div:nth-child(2) > input {
		font-size: 0.8rem;
		width: 70vw;
		max-width: 220px;
		max-height: 20px;
		height: 6vw;
	}
	.form-item div:nth-child(3) > input {
		font-size: 0.8rem;
		padding: 0.1rem;
		margin: 0.2rem 0rem;
		max-width: 120px;
	}
	.form-item div:nth-child(4) > input {
		font-size: 0.8rem;
		padding: 0.1rem 0.2rem;
	}
}
@media (min-width: 503px) {
	.form-item div:nth-child(2) > input {
		max-width: 330px;
		max-height: 32px;
		font-size: 1rem;
	}
	.form-item div:nth-child(3) > input {
		max-width: 1rem;
		padding: 0.2rem;
		margin: 0.3rem 0rem;
		max-width: 140px;
		font-size: 1rem;
	}
	.form-item div:nth-child(4) > input {
		font-size: 1rem;
		padding: 0.2rem;
	}
}
</style>
