### Regular expression
* \[aeiou\]
	* **character set**: any of a, e, i, o, u
	* gl==i==b j==o==cks v==e==x dw==a==rv==e==s!
* \[^aeiou\]
	* **negated set**: anything but a, e, i, o, u
	* ==gl==i==b== ==j==o==cks== ==v==e==x== ==dw==a==rv==e==s!==
* \[g-s\]
	* **range**: character between g & s
	* abcdef==ghijklmnopqrs==tuvwxyz
* .
	* **dot**: any character except newline \[^\n\r\]
		* ==glib jocks vex dwarves!==
* 