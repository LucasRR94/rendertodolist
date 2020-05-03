<script>
import FormItems from "./components/FormItems.vue";
import ListItems from "./components/ListItems.vue";
import { v4 as uuidv4 } from "uuid";

export default {
	name: "App",
	data() {
		return {
			items: []
		};
	},
	components: {
		FormItems,
		ListItems
	},
	render(createElement) {
		var self = this;
		return createElement(
			"div",
			{
				class: {
					app: true
				}
			},
			[
				createElement(
					"header",
					{
						class: {
							"main-header": true
						}
					},
					[createElement("h1", {}, "To do List")]
				),
				createElement("main", {}, [
					createElement(FormItems, {
						on: {
							newTodo: function(
								newTodoElement
							) {
								self.items.push(
									{
										idTodo: uuidv4(),
										description:
											newTodoElement[
												"description"
											],
										deadline:
											newTodoElement[
												"deadline"
											],
										newtodo:
											newTodoElement[
												"newtodo"
											]
									}
								);
								newTodoElement = {};
							}
						}
					}),
					createElement(ListItems, {
						props: {
							todos: self.items
						},
						on: {
							eliminateTodoItem: function(
								idtodoDelete
							) {
								console.log(
									idtodoDelete
								);
								self.items = self.items.filter(
									el => {
										console.log(
											el[
												"idTodo"
											]
										);
										return (
											el[
												"idTodo"
											] !==
											idtodoDelete
										);
									}
								);
							}
						}
					})
				]),
				createElement("footer", { footer: true }, [
					createElement(
						"p",
						{},
						"To do List, footer!"
					)
				])
			]
		);
	}
};
</script>

<style>
*,
html,
body {
	margin: 0 0;
	padding: 0 0;
	box-sizing: border-box;
}
.app {
	display: grid;
	grid-template-rows: 0.7fr 2.2fr 0.1fr;
	width: 100vw;
	height: 100vh;
}
.main-header {
	background: #007460;
	display: flex;
	flex: 1;
	align-content: center;
	justify-content: center;
	color: black;
	font-size: 1.3rem;
}
.main-header h1 {
	margin: 0.5rem;
	font-size: 4rem;
}
main {
	margin-bottom: 0.5rem;
	display: flex;
	flex-direction: column;
}
main div {
	margin: 0.1rem;
}
footer {
	height: 10vh;
	background: #007460;
	flex: 1;
	align-items: center;
	justify-content: flex-start;
}
footer p {
	margin: 1rem;
}
</style>
