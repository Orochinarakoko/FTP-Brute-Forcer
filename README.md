# FTP-Brute-Forcer
A basic python script that uses the threading and ftplib libraries in order to run a wordlist attack against an FTP server.
The code is almost identical to the SSH brute forcer script , except the action connecting mechanism.

# How it works
 - The user inputs the hostname/ip of the the owrdlist they want to use , ftp server , the name of the target user , and the number of threads that they want to spawn
 - The program then opens the wordlist , and reads every line in the file , and appends it to a queue ( from the queue module)
 - The program then spawns the desired number of threads that the user spawns
 - Each thread then gets a word from the word queue. Due to the fact that getting an element from the queue removes it from the queue, it means that multiple threads can run cocurrently , thus speeding up the attack.
 - The thread then tries to connect to the ftp server that the user inputs , using the inputted username , and the word from the wordlist
 - If the thread recevies a permission error, then we can determine that the password is not the word that was used.
 - If the thread cannot connect for some other reason , it will sleep for 1 minute.
 - If the thread connects successfully , then we can confirm that the current word is the users password , so the script tells the user the password.
 - The script runs in endless loop untill the user quits


# Troubleshooting

If the script runs , but does not


