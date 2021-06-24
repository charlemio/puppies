<script>
	import { fade } from 'svelte/transition';
	import Button from '../shared/button.svelte';

	let fields = { question: '', answerA: '', answerB: '' };
	let errors = { question: '', answerA: '', answerB: '' };

	const submitHandler = () => {
		//validate input
		let inputValid = false;
		if (fields.question.length > 0 && fields.answerA.length > 0 && fields.answerB.length > 0) {
			inputValid = true;
		} else {
			if (fields.question.length === 0) {
				errors.question = 'Should contain a question';
			}
			if (fields.answerA.length === 0) {
				errors.answerA = 'Should contain an answer';
			}
			if (fields.answerB.length === 0) {
				errors.answerB = 'Should contain an answer';
			}
		}

		if (inputValid) {
			//pass on info
			console.log(fields);

			// reset the fields
			fields.question = '';
			fields.answerA = '';
			fields.answerB = '';

			errors.question = '';
			errors.answerA = '';
			errors.answerB = '';
		} else {
			console.log('fix input');
		}
	};
</script>

<form in:fade="{{duration: 200}}" class="sm:text-lg sm:p-8" on:submit|preventDefault={submitHandler}>
	<div class="form-field">
		<label for="question">Poll Question:</label>
		<input type="text" id="question" bind:value={fields.question} placeholder={errors.question} />
	</div>
	<div class="form-field">
		<label for="answer-a">Answer A:</label>
		<input type="text" id="answer-a" bind:value={fields.answerA} placeholder={errors.answerA} />
	</div>
	<div class="form-field">
		<label for="answer-b">Answer B:</label>
		<input type="text" id="answer-b" bind:value={fields.answerB} placeholder={errors.answerB} />
	</div>
	<Button inverse><strong>Create Poll</strong></Button>
</form>

<style>
	form {
		/* max-width: 400px; */
		margin: 0 auto;
		text-align: center;
	}

	/* add 20px margin if viewport shrinks bellow 440px */
	@media (max-width: 440px) {
		form {
			margin: 0 20px;
		}
	}

	.form-field {
		display: flex;
		flex-direction: column;
		margin: 18px auto;
	}

	label {
		text-align: left;
	}

	input {
		width: 100%;
		padding: 12px;
		border-radius: 9px;
		outline: none;
		border: 2px solid gray;
	}

	input:focus {
		-webkit-appearance: none;
	}
</style>
