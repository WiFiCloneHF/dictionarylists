This is a bunch of dictionaries I have been making. I can't upload all of them due to the size however some important ones for WiFi passwords:

WiFi passwords are minimum length 8 characters long (as far as I know anywho) and as such people are inclined to put numbers on the end.

Important dictionaries. 
6 characters long capitals + 2 numbers 
5 characters long lowercase + 3 numbers

Then after both of those are done, you would want to run the entire English dictionary through with max 4 numbers at the end. This would be time consuming however so do the other two first.


An example of adding the 2 numbers on the end using hashcat.
On a 1080ti it took for 100 pmkids to run around 12 minutes.

hashcat64.exe -m 16800 pmkidfile.16800 -a 6 6letterenglishfirstlettercapitals.txt ?d?d

The same applies for 3 digits on the end for 5 character words.
hashcat64.exe -m 16800 pmkidfile.16800 -a 6 5letterenglishfirstlettercapitals.txt ?d?d?d


>> 
We would also want to run these alternatives that use no capitals. You can use rules for this however this is much easier in my opinion keeping track of files.

hashcat64.exe -m 16800 pmkidfile.16800 -a 6 6letterenglishnocapitals.txt ?d?d
hashcat64.exe -m 16800 pmkidfile.16800 -a 6 5letterenglishnocapitals.txt ?d?d?d

And of course the last command you would really need for the full English dictionary, i've filter out all words that are 7 characters or less.

hashcat64.exe -m 16800 pmkidfile.16800 -a 6 8plusenglishdictionary.txt ?d
hashcat64.exe -m 16800 pmkidfile.16800 -a 6 8plusenglishdictionary.txt ?d?d
hashcat64.exe -m 16800 pmkidfile.16800 -a 6 8plusenglishdictionary.txt ?d?d?d
hashcat64.exe -m 16800 pmkidfile.16800 -a 6 8plusenglishdictionary.txt ?d?d?d?d

Most people aren't going to have more than 4 digits on the end. 
