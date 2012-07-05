This module is bearly a module but more an exemple of a quick fix solution and I welcome anyone to make this better.
On my form i had to modify 2 select lists so i left both forms in this exemple
This is not a plug'n play solution, you will have to go into the module files to change a few things:

- in city_select_filter.module:
	-- line 12 you exposed filter form id
	-- line 16 and 17 the id of the widget (look for the select #id minus "edit-")
	-- line 21 and 32 same thing if you have another field to modify else delete that part
	-- line 45 put your vocabulary id


- in city_select_filter.js:
	-- 114 and 115 (remember I have 2 fields on my form) change the selector
	
	
So what city_select_filter.module does is unset an exposed filter field (a vocabulary select list) and creating a new set of options.
It doesn't matter if your select list shows hierachy or not as i am not using it at all because I manualy select the vocabulary ID.
so from a list like :

Cat 1
-Subcat 11
-Subcat 12
Cat 2
-Subcat 21
--Subcat 211
--Subcat 212
-Subcat 22

you get 

Cat 1
Cat 1 > Subcat 11
Cat 1 > Subcat 12
Cat 2
Cat 2 > Subcat 21
Cat 2 > Subcat 21 > Subcat 211
Cat 2 > Subcat 21 > Subcat 212
Cat 2 > Subcat 22


This new formatting allow us to use a little jquery plugin called <a href="https://github.com/AndrewIngram/jquery-select-hierarchy">jquery-select-hierarchy</a> and make the options conditionnal.

All this was inspired by @etcetera9 on this issue http://drupal.org/node/1170192#comment-6189032 and then has moved to http://drupal.org/node/1669940