<script>
export default {
	name: "ListItems",
	props: {
		todos: {
			type: Array,
			required: true
		}
	},
	data() {
		return {
			listTodos: []
		};
	},
	render(createElement) {
		var self = this;
		return createElement(
			"div",
			{
				class: "container-main-todo"
			},
			[
				createElement(
					"div",
					{
						class: "main-todo"
					},
					[
						createElement(
							"div",
							{
								class:
									"todo-header"
							},
							[
								createElement(
									"h1",
									{},
									"To do List"
								)
							]
						),
						createElement(
							"div",
							{
								class:
									"area-todo"
							},
							[
								createElement(
									"ul",
									{
										class:
											"list-todo"
									},
									[
										self.todos.map(
											el => {
												if (
													el[
														"newtodo"
													]
												) {
													return createElement(
														"li",
														{
															class:
																"toDo"
														},
														[
															createElement(
																"p",
																{},
																`Content: ${el["description"]}`
															),
															createElement(
																"p",
																{},
																`Deadline: ${el["deadline"]}`
															),
															createElement(
																"input",
																{
																	class:
																		"btn-clean-todo",
																	on: {
																		click: function(
																			e
																		) {
																			e.preventDefault();
																			self.$emit(
																				"eliminateTodoItem",
																				el[
																					"idTodo"
																				]
																			);
																		}
																	},
																	attrs: {
																		type:
																			"submit",
																		value:
																			"x"
																	}
																}
															)
														]
													);
												} else {
													return createElement(
														"p",
														{},
														el
													);
												}
											}
										)
									]
								)
							]
						)
					]
				)
			]
		);
	}
};
</script>

<style>
*,
html,
body {
	padding: 0 0;
	margin: 0 0;
	box-sizing: border-box;
}
.container-main-todo {
	width: 100vw;
	display: flex;
	flex: 1;
	flex-direction: row;
	justify-content: center;
}
.main-todo {
	border-radius: 0.6rem;
	width: 38vw;
	background-color: black;
	color: white;
	display: grid;
	justify-content: center;
	align-content: flex-start;
}
.todo-header {
	display: flex;
	flex: 1;
	justify-content: center;
}
.todo-header h1 {
	font-size: 2rem;
	margin: 0.8rem;
}
.area-todo {
	width: 36vw;
	color: #383b36;
}
.list-todo {
	display: flex;
	flex: 1;
	flex-direction: column;
	justify-content: center;
	align-content: center;
}
.toDo {
	border-radius: 0.6rem;
	background-color: #383b36;
	list-style-type: none;
	width: 34vw;
	height: 40vh;
	margin: 0.5rem;
	display: flex;
	flex: 1;
	flex-direction: column;
}
.toDo p {
	margin: 0.5rem;
	color: #fff;
}
.btn-clean-todo {
	border-radius: 1.1rem;
	width: 2.2rem;
	height: 2.2rem;
	color: black;
	margin: 0.5rem;
	border: none;
	background-color: red;
	font-size: 1.2rem;
}
@media (min-width: 320px) {
	.main-todo {
		width: 80vw;
		max-width: 500px;
	}
	.todo-header h1 {
		font-size: 1.5rem;
		margin: 0.5rem;
	}
	.area-todo {
		width: 76vw;
		max-width: 480px;
	}
	.toDo {
		margin: 0.2rem 0.2rem;
		width: 74vw;
		max-width: 460px;
	}
}
</style>
