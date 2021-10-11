# Useful for removing punctuation marks from multi-language sources or from text that may contain non-standard punctuation marks (such as emojis and pictographs). Tested in English, Japanese, Chinese, and Korean.

```python

from ml_punct_norm.normalizer import is_punct, strip_punct, replace_punct 

'''
is_punct(char)
Required argument -> char
Note: char must be a str type with length of 1.

'''

#Half-width period used in English, etc.
print("Half-width period is_punct -> {}".format(is_punct(".")))

#Full-width period used in Japanese, etc.
print("Full-width period is_punct -> {}".format(is_punct("。")))

#Hiragana character
print("Hiragana character is_punct -> {}".format(is_punct("あ")))

#Kanji
print("Kanji character is_punct -> {}".format(is_punct("私")))

#Emoji example
print("★ is_punct -> {}".format(is_punct("★")))


'''
strip_punct(input_str, input_skips = "")

This function strips all punctuation marks from a string.

Required argument -> input_str
input_str is the string from which punctuation marks are to be stripped. input_str must be specified as a str type.

Optional argument -> input_skips
input_skips is a string containing a sequence of punctuation marks that are not to be stripped from input_str. input_skips must be passed as a str type. 

'''

source_str = "This light-weight module, which also provides multi-language support, normalizes punctuation in strings."

#Strips all punctuation from source_str.
print(strip_punct(source_str))

#Strips all punctuation from source_str, except for hyphens.
print(strip_punct(source_str, "-"))

#Strips all punctuation from source_str, except for hyphens and commas.
print(strip_punct(source_str, "-,"))

japanese_str = "私は人間（にんげん）です。"

#Strips all punctuation from japanese_str.
print(strip_punct(japanese_str))

#Strips all punctuation from japanese_str, except for parentheses.
print(strip_punct(japanese_str, "（）"))

'''
replace_punct(input_str, input_skips = "", replacement= " ")

This function replaces all punctuation marks in a string with either a half-width space (default) or a user-specified string.

Required argument -> input_str
input_str is the string in which punctuation marks are to be replaced. input_str must be specified as a str type.

Optional arguments -> input_skips, replacement
input_skips is a string containing a sequence of punctuation marks that are not to be replaced with the replacement string. input_skips must be passed as a str type. 

replacement is a string that is used to replace punctuation marks (a half-width space by default). replacement must be specified as a str type. Note: If the replacement string follows a space or other substring that is equal to the replacement string, the replacement string will not be added (to avoid creating extra spaces/substrings in the string returned by the function). Also, in cases where multiple punctuations marks are used sequentially,
only a single instance of the replacement string will be used.

Note: There may be leading/trailing spaces in the string returned by the function, so you may want to use the strip() method if necessary.

'''
#Replaces all punctuation in source_str with a half-width space.
print(replace_punct(source_str))

#Replaces all punctuation in source_str with " <PUNCT> ".
print(replace_punct(source_str, replacement = " <PUNCT> "))

#Replaces all punctuation in japanese_str with a full-width space.
print(replace_punct(japanese_str, replacement = "　"))

#String with multiple punctuation marks. The extra spaces in the string are not normalized by the function.
multiple_punct_str = "Wha ... what are you     doing!?!?"

#Example in which multiple punctuation marks are used in a row.
print(replace_punct(multiple_punct_str))

#Example in which multiple punctuation marks are used in a row, with replacement passed as " <PUNCT> ".
print(replace_punct(multiple_punct_str, replacement = " <PUNCT> "))


```
