<script>
  import Button from "../shared/Button.svelte"; 
  import { createEventDispatcher } from "svelte";
  import { preventDefault } from "svelte/legacy";
  

 let dispatch = createEventDispatcher(); 
  let fields = {question: '', answerA: '',answerB: ''};
    let errors = {question: '', answerA: '',answerB: ''};
      let valid = false;

  const submitHandler  = () => { 
    valid = true;

    //validate question
       if(fields.question.trim().length < 5){
        valid = false;
        errors.question = 'Question must be at least five characters long' ;
       } else{
        errors.question = '';
       }
    //validate answer A
        if(fields.answerA.trim().length < 1){
        valid = false;
        errors.answerA = 'Answer A cannot be empty' ;
       } else{
        errors.answerA = '';
       }
    //validate answer B
        if(fields.answerB.trim().length < 1){
        valid = false;
        errors.answerB = 'Answer B cannot be empty' ;
       } else{
        errors.answerB = '';
       }
     id: Math//Add New Poll
    if (valid){
      let poll = {...fields, votesA: 0, votesB: 0,  id: Math.random()}
      dispatch ('add', poll);
    }

  }  
</script>

<form on:submit|preventDefault={submitHandler}>
 <div class="form-field">
    <label for="question">Poll Question</label>
    <input type="text" id="question" bind:value={fields.question}>
    <div class="error">{errors.question}</div>
 </div>
 <div class="form-field">
    <label for="answer-a">Answer A</label>
    <input type="text" id="answer-a" bind:value={fields.answerA}>
        <div class="error">{errors.answerA}</div>

 </div> 
 <div class="form-field">
    <label for="answer-b">Answer B</label>
    <input type="text" id="answer-b" bind:value={fields.answerB}>
        <div class="error">{errors.answerB}</div>

 </div>
 <Button type= "secondary" flat = {true} inverse = {false} >Add Poll</Button>
</form>

<style>
    form{
        padding: 20px 30px;
        border-radius: 8px;
        width: 45vh;
        margin-left: 30%;
        margin-right: 70%;
        margin-top: -25px; 
    }
    label{
        display: block;
        font-weight: bold;
        margin-top: 10px;
      }
  input[type="text"]{
    background-color: white;
    border-radius: 6px;
    font-weight: 900px;
    height: 2.5vh;
    border: 1px solid #ccc ;
    padding:10px;
    color: black;
    width: 45vh;
    margin-top: 10px;
  }   
  button{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 50%;
    margin-top: 20px;
  }
  .error{
    color: orangered;
    font-size: 14px;
    font-weight: bold;
  }
  .form-field{
    display: flex;
    flex-direction: column;
     margin-bottom: 15px;
  }
  @media (max-width: 768px) {
    form {
      width: 45vh;
      margin-left: 10%;
      margin-right: 10%;
      padding: 1rem;
    }
    input[type="text"] {
      width: 100%;
    }
    button {
      margin-left: 0;
      width: 100%;
    }
  }                     
</style>