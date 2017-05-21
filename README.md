# Web scraping using Ruby 

Let's do some configuration before starting hacking around web data:

1. Download and install one of the following drivers based on the browser you are using:

* [Geckodriver](https://github.com/mozilla/geckodriver/releases) for chrome:  

```
$ cd /usr/local/bin/
$ sudo wegt https://chromedriver.storage.googleapis.com/2.29/chromedriver_linux64.zip
$ sudo unzip -xzvf chromedriver_linux64.zip
$ sudo rm chromedriver_linux64.zip
```

* [Chromedriver](https://chromedriver.storage.googleapis.com/index.html?path=2.29/) for firefox: 

```
$ cd /usr/local/bin/
$ sudo wegt https://github.com/mozilla/geckodriver/releases/download/v0.16.1/geckodriver-v0.16.1-linux64.tar.gz
$ sudo tar -xzvf geckodriver-v0.16.1-linux64.tar.gz
$ sudo rm geckodriver-v0.16.1-linux64.tar.gz
```

2. Create a rails project or just clone this repo:

* In case you wanna start on your own you have to install these two gems:

```
gem 'pry-rails'
gem 'watir'
```

* Otherwise just clone the current repo, then cd into and type rails console 

```linux
cd web_scraper/
rails console
```
The open the browser

```ruby 
pry(main)> browser = Watir::Browser.new :firefox # or :chrome
```

And now we are ready for scarping by covering five different scenarios.

## Use case 1 — Static content

```ruby
pry(main)> require ("opne-uri")

# Targeted page that we are gonna srape 

pry(main)> endpoint = "http://www.basketball-reference.com/players/c/curryst01/gamelog/2016/"

# Open the the page on the browser

pry(main)> browser.goto endpoint

# Parse the HTML page using Nokogiri to have full control of its data structure (string representation of HTML)

pry(main)> document = Nokogiri::HTML.parse(open(endpoint))

# Get the biggest table that contains the data we need 

pry(main)> games_table = document.css("table").sort { |x,y| y.css("tr").count <=> x.css("tr").count }.first

# Grap the 3 pointers made and attempted (columns 14 and 15) with removing null values

pry(main)> data = rows.map do |row|
 [row.at_css("td:nth-child(14)").try(:text), row.at_css("td:nth-child(15)").try(:text)]
end 

pry(main)> data = data.reject { |tuple| tuple[0].nil?}

```
The result:

```ruby
=> [["12", ".417"],
 ["9", ".444"],
 ["14", ".571"],
 ["8", ".500"],
 ["11", ".636"],
 ["16", ".500"],
 ["10", ".200"],
 ["7", ".429"],
 ["10", ".300"],
 ["13", ".615"],
 ["16", ".313"],
:
```


## Scenario 2 — Static content

```ruby
# Given the following list of players 
pry(main)> players = ["kevin durant", "stephen curry", "klay thompson", "david west", "ian clark"]

# Let's autmate the process of getting an image for each player 

pry(main)> players_images = players.map do |player|
pry(main)*   br.goto("images.google.com")
pry(main)*   br.text_field(title: "Search").set player
pry(main)*   br.button(type: "submit").click
pry(main)*   sleep 1
pry(main)*   document = Nokogiri::HTML.parse(br.html)
pry(main)*   document.at_css("div#ires img")["src"]
pry(main)*   end
```

The result:

```ruby
=> ["https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcST0nA71N5t1EuWShgB6kcQWp9gITcbWj1ozRHPAOkg5VJO83nKJU82xgvH",
 "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTFFUSofO0zmFy-TVW_ShD4WB724mitg59M2Y8Qh7rJuCUqB8XwGpgVGxbP",
 "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTeu2IopG5CQ_6TwTxtTtpG9Mtb9j55nJXN83Y8wjzepo4KThkfRJRcYU44",
 "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSlrL9UnBk3AXRbfQ-hnIQ9LFoRJrdbswwXWfE2M99ZMlly-1JFJC_EPoD1",
 "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQJ97P-97KU9h9dN1pCkJmHDSAve2tWtBdvgW-TvEtPYzB-IEGTEUO2Hqxk"]
```

## Scenario 3 — JavaScript injection

```ruby
pry(main)> endpoint = "http://stats.nba.com/game/#!/0021500548/playbyplay/"
```

## Scenario 4 — Static content

## Scenario 4 — Static content
