<script>
    import Button from "../lib/button.svelte";
    import Card from "../lib/card.svelte";
    // import PollStore from "../stores/PollStore.js";
    // import { createEventDispatcher } from "svelte";

    // let dispatch = createEventDispatcher();

    // let fields = {
    //     question: "",
    //     answerA: "",
    //     answerB: "",
    // };

    // let errors = {
    //     question: "",
    //     answerA: "",
    //     answerB: "",
    // };

    // let valid = false;

    // const submitFormHandler = () => {
    //     valid = true;

    //validations
    //     if (fields.question.trim().length < 5) {
    //         valid = false;
    //         errors.question = "This field must contain at least 5 characters";
    //     } else {
    //         errors.question = "";
    //     }

    //     if (fields.answerA.trim().length < 1) {
    //         valid = false;
    //         errors.answerA = "This field cannot be empty";
    //     } else {
    //         errors.answerA = "";
    //     }

    //     if (fields.answerB.trim().length < 1) {
    //         valid = false;
    //         errors.answerB = "This field cannot be empty";
    //     } else {
    //         errors.answerB = "";
    //     }

    //     if (valid) {
    //         let poll = { ...fields, votesA: 0, votesB: 0, id: Math.random() };
    //         console.log(fields);
    //         PollStore.update((currentPolls) => [poll, ...currentPolls]);
    //         dispatch("addPoll");
    //     }
    // }; -->
    let question = "";
    const submitFormHandler = () => {
        console.log(question);

        const completeQuestion = {
            question,
            is_reply: false,
        };

        fetch("http://192.168.4.111:4000/api/questions", {
            method: "POST",
            body: JSON.stringify(question),
            mode: "cors",
            headers: {
                "Content-Type": "application/json/",
            },
        });
    };
</script>

<Card>
    <div class="flex justify-center items-center mt-40">
        <form on:submit|preventDefault={submitFormHandler}>
            <div class="flex flex-col">
                <label
                    for="question"
                    class="font-medium text-dark-gray-800 text-3xl"
                    >Ask Your Question</label
                >
                <input
                    class="border mb-3 p-10"
                    type="text"
                    id="question"
                    bind:value={question}
                />
                <!-- <p class="error-message">{errors.question}</p> -->
            </div>
            <Button>Submit Question</Button>
        </form>
    </div>
</Card>

<style>
    form {
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }

    label {
        margin: 10px auto;
        text-align: left;
    }
    /* .error-message {
        color: #d91b42;
    }
    .error {
        border: 1px solid #d91b42;
    } */
</style>
