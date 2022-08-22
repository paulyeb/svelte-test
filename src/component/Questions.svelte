<script context="module">
    export async function load({ fetch }) {
        const res = await fetch("http://192.168.4.111:4000/api/questions");
        const questions = await res.json();

        if (res.ok) {
            return {
                props: {
                    questions,
                },
            };
        }

        return {
            status: res.status,
            error: new Error("Could not find any questions"),
        };
    }
</script>

<script>
    export let questions;

    let questionsArray = [];

    if (questions) {
        questionsArray = questionsArray.push(fetchedQuestion);
    }
</script>

<div>
    <ul>
        {#each questions as question (question.id)}
            <li>{question.question}</li>
        {/each}
    </ul>
</div>
