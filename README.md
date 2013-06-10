# Welcome to `formula1.db`

A free open public domain Formula 1/Formula One database & schema
for use in any (programming) language
(e.g. uses plain text fixtures/data sets). Example:


~~~
### Drivers

Sebastian Vettel|S. Vettel|Vettel,  3 Jul 1987, VET,  Heppenheim | Hesse,  de
Fernando Alonso,  29 Jul 1981,  ALO,  Oviedo | Asturias,   es
Kimi Räikkönen,   17 Oct 1979,   Espoo,  fi
...
~~~

~~~
### Squads

(1) Sebastian Vettel  /   Red Bull
(2) Mark Webber       /   Red Bull

(3) Fernando Alonso   /   Ferrari
(4) Felipe Massa      /   Ferrari
...
~~~

~~~
### Circuits

au, Grand Prix Australia (Melbourne Circuit)|GP Australia, AUS, Melbourne, au
jp, Grand Prix Japan (Suzuka Circuit)|GP Japan, JPN, Suzuka, jp
mc, Grand Prix Monaco (Circuit de Monaco), MON, Monte Carlo, mc
...
~~~

~~~
### Races - Formula 1 Calendar 2013

(1) Sun 17 Mar 2013 17:00  / Grand Prix Australia
(2) Sun 24 Mar 2013 16:00  / Grand Prix Malaysia
...
~~~

~~~
### Records - Grand Prix Monaco 2013

1  Nico Rosberg      Mercedes     78    2:17:52.056
2  Sebastian Vettel  Red Bull     78  +3.8 secs
3  Mark Webber       Red Bull     78  +6.3 secs
4  Lewis Hamilton    Mercedes     78  +13.8 secs
...
~~~~



## Usage

Build yourself a copy of the `formula1.db` from the plain text fixtures in three steps.

Step 1: Get a copy of the `world.db` fixtures

    $ git clone git://github.com/geraldb/world.db.git

Step 2: Get a copy the `formula1.db` fixtures

    $ git clone git://github.com/geraldb/formula1.db.git

Step 3: Let's build the `formula1.db`

    $ sportdb setup --include ./formula1.db --worldinclude ./world.db --dbname formula1.db

That's it.


## Tables, Schema

The `formula1.db` includes the following tables:

* [teams](teams/txt) (e.g. Red Bull, Ferrari, McLaren, etc.)
* [tracks](circuits.txt) (also known as circuits e.g. GP Australia, GP Japan, GP Monaco, etc.)
* [persons](drivers.txt) (also known as drivers e.g. Sebastian Vettel, Fernando Alonso, Kimi Räikkönen, etc.)
* [rosters](2013/squads.txt) (join table team+person+event also known as squads e.g. 2013  Red Bull  Sebastian Vettel, etc.)
* [races](2013/races.txt) (join table event+track e.g. GP Australia 2013, GP Japan 2013, etc.)
* [records](2013/06-gp-monaco.txt) (join table race+person e.g. 1  Sebastian Vettel  Red Bull  70  1:32:09.143, etc.)


## How to use `formula1.db` in Ruby

Driver Model

~~~
vettel = Person.find_by_key( 'sebastianvettel')

vettel.name
=> 'Sebastian Vettel'

by.country.title
=> 'Germany'
~~~

Circuit Model

~~~
jp = Track.find_by_key( 'jp')

jp.title
=> 'Grand Prix Japan (Suzuka Circuit)'

jp.country.title
=> 'Japan'
~~~

and so on.

## License

The `forumla1.db` schema, data and scripts are dedicated to the public domain.
Use it as you please with no restrictions whatsoever.

## Questions? Comments?

Send them along to the [Open Sports Database & Friends Forum/Mailing List](http://groups.google.com/group/opensport). Thanks!
