I want to replace Ulysses with a _free_ software. That software must use Markdown, and be able to manage multiple files. 
So:
- sublime with the markdown function
- evernote specialty of managing files
- sublime also has an extension that exchanges the information between them

The combanition is perfect, maybe even more powerful than Ulysses. No wonder they comes to the first choice.

#### [sublime-evernote](https://github.com/bordaigorl/sublime-evernote).
This extension makes markdown notes and add them to evernote. And it's the best among competitors. Not only add notes to evernote, it can also read your notes from evernote and modify them. Only one function lacked, managing notebooks. Otherwise it can be called full-funtion.

But I got problem that costs hours to solve. Firstly, the inline code was found unformatted. But with another app called [Marxico](http://marxi.co/), that was normally functioned as below.
![Marxico](http://i.imgur.com/xABr0T4.png)

So the problem should be on the sublime settings or _sublime-evernote_ side. I just want to see how the normal functioning file of Marxico would behave on sublime-evernote, when it prompts that a problem encountered and suggests me to go to [issues page](https://github.com/bordaigorl/sublime-evernote/issues) on github.

There I just met the same question! The extension maker had already solved the problem 8 days ago in the `devel` banch.

So "get the devel branch and the problem would be solved", I was thinking at that time. But it was far from the truth. I spend about another hour on the "simple" process. The final mistake that I made was, the wrong directory!!!

But some were learnt,
1. CSS settings
  * to specific type on the website
  * structure is kind of dictionary in Python
2. About the user preference
  * stored in `/Users/liubo/Library/Application Support/Sublime Text 3/Packages/User`
  * Key binding
  * User preference
  * User preference of packages
  * Possibly the future package preference would be stored here


ac
2014-10-22
