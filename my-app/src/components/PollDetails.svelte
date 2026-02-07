<script>
  import { createEventDispatcher } from 'svelte';
  import Card from '../shared/Card.svelte';
 export let poll;
 const dispatch = createEventDispatcher();
 //reactive values
$: totalVotes = Number(poll.votesA) + Number(poll.votesB);
$: percentA = Math.floor(100 / totalVotes * poll.votesA);
$: percentB = Math.floor(100 / totalVotes * poll.votesB);



//handling votes
const handleVote = (option, id) => {
  dispatch('vote', {option, id});
};


</script>





<Card>
  <div class = "poll">
    <h3>{ poll.question }</h3>
    <p> Total votes: { totalVotes }</p>
      <div class="answer" on:click={() => handleVote('a', poll.id)}>
        <div class="percent percent-a" style="width: {percentA}%"></div>
        <span> {poll.answerA} ({poll.votesA})</span>
      </div>    
     <div class="answer"  on:click={() => handleVote('b', poll.id)}>
        <div class="percent percent-b" style="width: {percentB}%"></div>
        <span> {poll.answerB} ({poll.votesB})</span>
      </div> <br>
</div>
</Card>

<style>
    .poll {
      width: 50vh;
  gap: 2rem;
  padding: 20px;
  border-radius: 8px;
}

.answer {
  display: flex;
  align-items: center;
  margin-top: 10px ;
  background-color: #fafafa;
  cursor: pointer;
  padding: 0.8rem;
  position: relative;
}
.answer:hover{
  opacity: 0.6;
}
span{
  display: inline-block;
  padding: 5px 10px;

}
.percent {
  height: 100%;
  position: absolute;
  box-sizing: border-box;
}


.percent-a{
  margin-left: -0.53rem;
  border-left: 6px solid red;
  background-color: rgba(217, 27,66, 0.2);
}
.percent-b{
  margin-left: -0.53rem;
  border-left: 6px solid green;
  background-color: rgba(69, 196, 150, 0.2);
}
</style>