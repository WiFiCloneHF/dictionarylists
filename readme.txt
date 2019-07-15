Note: When doing the malefemale all names (the names are repeated 3 times, one with first letter capital, one with all capitals and one with no capitals such as
Jordan
jordan
JORDAN
I'd recommend running the wordlist 2-3 times with ?d / ?d?d / ?d?d?d 
Each one respectively will do
Jordan1
Jordan11
Jordan111


My preferred order of running these on a single 1080ti.

###CapandNoCap7letterwords.txt ?d (4 minutes)
>>7letterenglishnocapitals.txt ?d (2 minutes)
>>7letterenglishfirstlettercapitals.txt ?d (2 minutes)


###CapandNoCap6letterwords.txt ?d?d (20 minutes)
>>6letterenglishnocapitals.txt ?d?d (12 minutes)
>>6letterenglishfirstlettercapitals.txt ?d?d (12 minutes)


###CapandNoCap5letterwords.txt ?d?d?d (3 hours)
>>5letterenglishnocapitals.txt ?d?d?d (2 hours)
>>5letterenglishfirstlettercapitals.txt ?d?d?d (2 hours)





###8plusenglishdictionary.txt	(1 minute)


But if you really want to get fancy then you can try the below which will try add numbers to the end of all English words over 8 characters long already.

8plusenglishdictionary.txt ?d (8 minutes)
8plusenglishdictionary.txt ?d?d
8plusenglishdictionary.txt ?d?d?d
8plusenglishdictionary.txt ?d?d?d?d

Then I would recommend an 8 digits long file. It's 1gb or just under. I can't upload to github. To create it yourself:
crunch 8 8 1234567890 -o 8digitslong.txt

If you don't want 2 numbers to repeat you can add the -d 1 toggle like so
crunch 8 8 1234567890 -o 8digitslong.txt -d 1

This will never make 
00000000
Instead it will do something like
01010101




>>
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
