<script>
    import FeedbackForm from './components/FeedbackForm.svelte'
    import FeedbackList from './components/FeedbackList.svelte'
    import FeedbackStats from './components/FeedbackStats.svelte'

    let feedback = [
        {
            id: 1,
            rating: 10,
            text: 'lorem ipsum',
        },
        {
            id: 2,
            rating: 6,
            text: 'morem ipsum',
        },
        {
            id: 3,
            rating: 3,
            text: 'norem ipsum',
        },
        {
            id: 4,
            rating: 9,
            text: 'porem ipsum',
        }
    ]

    $: count = feedback.length
    $: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length

    const addFeedback = (e) => {
        const newFeedback = e.detail
        feedback = [newFeedback, ...feedback]
    }

    const deleteFeedback = (e) => {
        const itemId = e.detail
        feedback = feedback.filter((item) => item.id != itemId)
    }
</script>

<main class="container">
    <FeedbackForm on:add-feedback={addFeedback} />
    <FeedbackStats {count} {average} />
    <FeedbackList feedback={feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>

</style>