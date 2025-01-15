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

If the script runs , but does not return a password:
 - The wordlist may be insufficient. Try a larger wordlist
 - If a larger wordlist fails , use crunch to make a wordlist of every possible combination . NOTE THIS WOULD MOST LIKELY TAKE AN IMPRACTICAL AMOUNT OF TIME
 - Check that you have entered the username correctly

If the script freezes:
 - Try running the script with fewer threads.
 - Check you have entered the ip/hostname of the server correctly
 - Check that the server is running , and is responsive using ping.
 - Check , if you are connecting over internet, that your internat connection is sufficent / working

If recieving FAILED TO CONNECT : THREAD WILL SLEEP FOR 1 MINUTE:
 - If this only occurs rarely , not to all threads , then it can be ignored
 - Try running the script again , with fewer threads - I reccommend NO MORE THAN 20 , or else your attemps to connect may be stopped.
 - Check that you are connected to the internet

If you encounter any other errors when using this script , feel free to conact me and I will attempt to amend it.


