# Overthewire-Bandit-Level-0-Level-10
This is my level 0 to level 10 overthewire labs for the Bandit section where I learn the linux commands as I find passwords to unlock the next level.

At level 0 the first obstacle I faced was trying to connect using ssh using a specific port. I tried to run the telnet command in my PowerShell but it was not connecting and this was because of a windows feature that I had to enable in my machine.

The command to log into the game was `ssh -p [port number] [username]@[ip/url]`

After logging into the game I was now meant to run specific linux commands according to the requirements listed.

I got to a level where the file was dash-named, meaning when I ran ls it returned - and you cannot do cat - to read the file because it is a special character. Therefore with the help of Google I figure out how to read special character named files 

The command should have ./ at the beginning so that you can be able to read the dashed file
`cat ./- `

Next I came across a file that was named with spaces and in order to read this file you had to use " " and ./
`cat "./--spaces in this filename--`

I also learnt how to find human readable files. The find command is what was to be used using the grep condition of finding files that contain text/ASCII
`find . -type f -exec file {} + | grep -E "text|ASCII`

The command `ls -la` will allow you to see all the details of the files in that directory including the size and the controls put in place. (rwx) r - read, w - write, x - execute

Also the find command can be used to specify what are you searching for. If it a specific group assigned or user assigned
`find / -type f -group bandit6 -user bandit7`

The grep command can be used to also narrow down the search in a file if there is a plethora of data in the file.
`cat data.txt | grep millionth` - this reads the data.txt file by searching for the word millionth. It helped narrow down because the file had multiple data that would be time consuming reading through all of them.

A command that was interesting was the sort and the uniq -u. The order of calling these commands makes the difference; you sort first then find the unique character in the file that is only found once. If you did the inverse the unique entry will not be singled out.
`cat data.txt | sort | uniq -u` 
Sort arranges identical entries next to each other then uniq examines consecutive lines. -u displays only lines that occur once.

The last 2 commands I learnt was the strings and the base64 command. The strings command should return the data in the file that is a series of non readable icons into strings that can be human readable.
`cat data.txt | strings` and the base64 command is run by itself directly to read the file and return the data in the file in the base64 format.
`base64 -d data.txt ` -d means decode.
