<script>
    import Button from "../lib/button.svelte";
    import Card from "../lib/card.svelte";

    let question = "";
    const submitFormHandler = () => {
        console.log(question);

        const allQuestionDetails = {
            question,
            is_reply: false,
            reply_to: 0,
            upvotes: 0,
            downvotes: 0,
        };

        console.log(allQuestionDetails);

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
