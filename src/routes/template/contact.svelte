<script>
    import { onMount } from 'svelte';
    /**
     * @type {HTMLElement | null}
     */
    let form; 
    /**
     * @type {HTMLElement | null}
     */
    let result; 

    onMount(() => {
        form = document.getElementById('form');
        result = document.getElementById('result');

        // Move the event listener inside the onMount function
        if (form) {
            form.addEventListener('submit', function(e) {
              e.preventDefault();
              // @ts-ignore
              const formData = new FormData(form);
              const object = Object.fromEntries(formData);
              const json = JSON.stringify(object);
              // @ts-ignore
              result.innerHTML = "Please wait...";

              fetch('https://api.web3forms.com/submit', {
                      method: 'POST',
                      headers: {
                          'Content-Type': 'application/json',
                          'Accept': 'application/json'
                      },
                      body: json
                  })
                  .then(async (response) => {
                      let json = await response.json();
                      if (response.status == 200) {
                          // @ts-ignore
                          result.innerHTML = json.message;
                      } else {
                          console.log(response);
                          // @ts-ignore
                          result.innerHTML = json.message;
                      }
                  })
                  .catch(error => {
                      console.log(error);
                      // @ts-ignore
                      result.innerHTML = "Something went wrong!";
                  })
                  .then(function() {
                      // @ts-ignore
                      form.reset();
                      setTimeout(() => {
                          // @ts-ignore
                          result.innerHTML = "Message sent!"
                      }, 3000);
                  });
            });
        }
    });
</script>

<div class="contact">
    <slot />
    <form method="POST" id="form">
        <input type="hidden" name="access_key" value="69926972-d700-4548-8e7b-705960468f99">
      
        <!-- Optional: Subject an be prefilled using type="hidden"
             or type="text" for normal user submitted input -->
        <input type="hidden" name="subject" value="New Submission from Web3Forms">
      
        <!-- Optional: From Name you want to see in the email
             Default is "Notifications". you can overwrite here -->
        <input type="hidden" name="from_name" value="Principle Air Website">

        <input type="checkbox" name="botcheck" class="hidden" style="display: none;">
      
        <!-- Custom Form Data: Form data you wish to receive in email. -->
        <input type="text" name="First Name" required placeholder="Name">
        <input type="text" name="Last Name" required placeholder="Last Name">
        <input type="text" name="Address" placeholder="Address">
        <input type="email" name="email" required placeholder="Email">
        <input type="text" name="Phone Number" required placeholder="Phone Number">
        <textarea name="message" required placeholder="Message"></textarea>
      
        <button type="submit">Submit Form</button>
        <div id="result"></div>
      
      </form>
</div>

<style>
    .contact { 
        display: flex; 
        position: relative; 
        flex-direction: column; 
        height: 100%; 
    }   
    input { 
        flex-grow: 0;   
        position: relative; 
        background: none;
        border-right: none; 
        color: inherit;
        margin: 3vw; 
        font-size: 2vh; 
        font-family: inherit; 
    }
    input::selection { 
        border: none; 
        border-bottom: 1px white;
    }
    textarea { 
        background: none;
        color: inherit;
        font-family: inherit;
        resize: none;
        width: 80%;
        flex-grow: 2;
        display: flex; 
        margin: 2vw; margin-left: 3vw;
        font-size: 2vh;
        flex: 1 1 0px;
    }
    button { 
        font-family: inherit; 
        color: inherit; 
        border: none; 
        background-color: rgba(255, 255, 255, 0.13);
        padding: 0.5vw; 
        font-size: 2vh;     
        transition: background-color 1s ease-out;
        margin: 2vw; margin-left: 3vw;
    }
    button:hover { 
        color: rgb(32, 32, 32); 
        background-color: white; 
    }
    #result { 
        padding-left: 3vw; 
        font-size: 2vh; 
    }
</style>