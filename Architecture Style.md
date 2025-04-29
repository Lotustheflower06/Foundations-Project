**Architecture Style**  
The architecture style I plan on using is a layered approach. Layered architecture is kinda like a sandwich. There's different layers that do different things and achieves an overall goal. A layered design is also good for my project because it's fairly secure compared to other models because you can isolate the steps the program takes since it goes top to bottom.  

**Logical Components**  
The logical components of the project will be the random module, encryption for the saved passwords, and time sensitivity. Here's some pseudo-code to show what I think it would look like:  

**OTP Generator:**  

    Initialize OTP Generator:
    Input: secret_key (shared between server and user)
    Input: time_step (default 30 seconds)

    Function generate_current_otp(secret_key, time_step):
        current_time = get current Unix timestamp
        time_counter = current_time divided by time_step
        otp = HMAC(secret_key, time_counter)
         otp = truncate otp to 6 digits
    Return otp

    Main loop:
     Load secret_key
     While true:
         current_otp = generate_current_otp(secret_key, time_step)
          Display current_otp
         Wait until time_step boundary changes
         
**Password Manager**  

    Initialize Password Manager:
     Input: master_password
     key = derive_key(master_password)

    Load encrypted database:
     If database file exists:
            decrypt database using key
            load passwords into memory
        Else:
            create empty password store

    Main Menu:
     While true:
         Display options:
                (1) Add new password
                (2) Retrieve a password
             (3) Delete a password
             (4) Save and exit

            Input: user_choice

            If user_choice == 1:
                Input: service_name
             Input: username
             Input: password (or generate random password)
             Add entry to password store

         Else if user_choice == 2:
             Input: service_name
             If service_name exists:
                 Display username and password
             Else:
                 Show "Service not found."

            Else if user_choice == 3:
                Input: service_name
             If service_name exists:
                Delete entry
             Else:
                 Show "Service not found."

            Else if user_choice == 4:
              Encrypt password store using key
             Save to file
                Exit program

         Else:
             Show "Invalid choice."
             
   The programming language I'd choose for this project would be Java because its pretty secure.
   
   

