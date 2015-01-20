

# Background
Break texts into sentence is not easy. And the importance is roared when all your result are based on it. So I digged deep into the regex usage in breaking text into sentence. I didn't find a good result. But with the help of [regex101](https://regex101.com), I got a flexiable so that 'perfect' expression as below.

You can also test code at the end of this article. But I recommand [regex101.com](regex101.com)

###################################
# This is the regex expression
`(?<!ca.)(?<!vs.)(?<!\w\.\w.)(?<![A-Z][a-z]\.)(?<![A-Z][a-z][a-z]\.)(?<![A-Z][a-z][a-z][a-z]\.)((?<=[.!?])|(?<=[.!?][\'"]))[\s]{1,20}((?=[A-Z])|(?=[0-9])|(?=\"))`

## Raw text:
"
Auch für 2013 und z.B. 2014 gehen wir wieder von einem hohen Free Cash Flow aus. Die Mehrheit der Mittelabflüsse im Zuge des Effizienzsteigerungsprogramms werden 2013 zahlbar und dürften gegenüber 2012 zusätzliche Zahlungsmittelabflüsse von ca. 300 Mio € mit sich bringen, usw.

"such dreadful ones." Surely!

Mr. Liu
Mrs. Pang
Prof. Thurner

Juve vs. Milan

apple, banana, pear etc. "Oh God!"
"

## Result:
I got 5 matches which are
1. aus. Die
2. usw. "such
3. dreadful ones."
4. Surely!
5. pear etc. "Oh God!"

# Explaination
. `(?<!ca.)`  #exception: ca.(German)
. `(?<!vs.)`  #exception: vs.
. `(?<!\w\.\w.)`  #short names: U.S.
. `(?<![A-Z][a-z]\.)`  #such as Mr.
. `(?<![A-Z][a-z][a-z])` #such as Mrs., Sir.
. `(?<![A-Z][a-z][a-z][a-z])` #such as Prof.
. `((?<=[.!?])|(?<=[.!?][\'"]))`  #sentence ends with ".!?" and quotes
. `[\s]{1,20}`  #empty space.Taking into account for unregular text, allow it to happen more than one time, up to 20.
. `((?=[A-Z])|(?=[0-9])|(?=\"))`  #match the next sentence's beginning

# Explaination of regex syntax
. `(?<!)`, negative look behind, means that it is not possible to match patterns inside the bracket.
. `(?<=)`, positive look behind, means that patterns inside bracket can be matched.
. `(?=)`, positive look ahead, mean that patterns inside bracket can be matched.

# Code of example
```python
import re
p = re.compile(ur'(?<!ca.)(?<!vs.)(?<!\w\.\w.)(?<![A-Z][a-z]\.)(?<![A-Z][a-z][a-z]\.)(?<![A-Z][a-z][a-z][a-z]\.)((?<=[.!?])|(?<=[.!?][\'"]))[\s]{1,20}((?=[A-Z])|(?=[0-9])|(?=\"))')
test_str = u"Auch für 2013 und z.B. 2014 gehen wir wieder von einem hohen Free Cash Flow aus. Die Mehrheit der Mittelabflüsse im Zuge des Effizienzsteigerungsprogramms werden 2013 zahlbar und dürften gegenüber 2012 zusätzliche Zahlungsmittelabflüsse von ca. 300 Mio € mit sich bringen, usw.\n\n\"such dreadful ones.\" Surely!\n\nMr. Liu\nMrs. Pang\nProf. Thurner\n\nJuve vs. Milan\n\napple, banana, pear etc. \"Oh God!\""
 
re.findall(p, test_str)
```
