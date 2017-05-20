# Web scraping using Ruby 

Few steps before starting hacking around web data:

1. Install one of the following drivers based on the browser you are using:

* Download and install [geckodriver](https://github.com/mozilla/geckodriver/releases) for chrome:  

```
cd /usr/local/bin/
sudo wegt https://github.com/mozilla/geckodriver/releases/download/v0.16.1/geckodriver-v0.16.1-linux64.tar.gz
sudo tar -xzvf geckodriver-v0.16.1-linux64.tar.gz
sudo rm geckodriver-v0.16.1-linux64.tar.gz
```

* Download and install [geckodriver](https://github.com/mozilla/geckodriver/releases) for firefox: 

```
cd /usr/local/bin/
sudo wegt https://github.com/mozilla/geckodriver/releases/download/v0.16.1/geckodriver-v0.16.1-linux64.tar.gz
sudo tar -xzvf geckodriver-v0.16.1-linux64.tar.gz
sudo rm geckodriver-v0.16.1-linux64.tar.gz
```

3. Create rails project or clone this repo and start scraping:

* In case you wanna start a new rails project you have to install these two gems:

```
gem 'pry-rails'
gem 'watir'
```

* Otherwise just clone the current repo, then cd into web_scraper directory and type rails console 

```linux
cd web_scraper/
rails console
```
```ruby 

```

## Scenario 1 — Static content

```ruby
pry(main)> require ("opne-uri")

# Get the page 
pry(main)> endpoint = "http://www.basketball-reference.com/players/c/curryst01/gamelog/2016"

# Get the HTML page as a Nokogiri document 
pry(main)> doc = Nokogiri::HTMLparse(open(endpoint))
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
 ["10", ".500"],
 ["14", ".429"],
 ["11", ".273"],
 ["8", ".375"],
 ["12", ".333"],
 ["16", ".563"],
 ["6", ".500"],
 ["8", ".500"],
 ["11", ".727"],
 ["15", ".600"],
 ["9", ".556"],
 ["10", ".300"],
 ["13", ".462"],
 ["9", ".222"],
 ["5", ".400"],
 ["6", ".333"],
 ["8", ".250"],
 ["4", ".250"],
 ["13", ".462"],
 ["5", ".200"],
 ["10", ".500"],
 ["8", ".500"],
 ["11", ".364"],
 ["14", ".571"],
 ["11", ".364"],
 ["12", ".417"],
 ["16", ".500"],
 ["15", ".467"],
 ["12", ".583"],
 ["9", ".333"],
 ["15", ".533"],
 ["9", ".667"],
 ["7", ".429"],
 ["11", ".455"],
 ["11", ".273"],
 ["15", ".733"],
:
```


## Scenario 2 — Static content

## Scenario 3 — Static content

## Scenario 4 — Static content

## Scenario 4 — Static content
