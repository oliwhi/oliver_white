---
layout: article
title: ChatBot
show_title: true
tags: Research
catagory: research
---
<!-- Gen via ChatGPT, need to input API keys etc. -->
<form id="chat-form">
  <label for="chat-input">Type your message:</label>
  <input type="text" id="chat-input" name="user-message">
  <button type="submit">Send</button>
</form>

<!-- Next, create an HTML element to display the chat messages -->
<div id="chat-container"></div>

<!-- Add a script tag at the end of your HTML body -->
<script>
  const chatForm = document.querySelector('#chat-form');
  const chatInput = document.querySelector('#chat-input');
  const chatContainer = document.querySelector('#chat-container');

  chatForm.addEventListener('submit', async (event) => {
    event.preventDefault();

    // Get the user's message from the input field
    const userMessage = chatInput.value;

    // Send a POST request to the ChatGPT server with the user's message
    const response = await fetch('https://free.churchless.tech/v1/chat/completions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': '' // Replace with your API key
      },
      body: JSON.stringify({
        prompt: userMessage,
        max_tokens: 60,
        n: 1,
        stop: '\n'
      })
    });

    // Get the response from the ChatGPT server
    const json = await response.json();
    const botMessage = json.choices[0].text.trim();

    // Clear the input field and display the bot's message
    chatInput.value = '';
    const messageBubble = document.createElement('div');
    messageBubble.classList.add('message-bubble');
    messageBubble.textContent = botMessage;
    chatContainer.appendChild(messageBubble);
  });
</script>
