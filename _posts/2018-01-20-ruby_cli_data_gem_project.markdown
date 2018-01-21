---
layout: post
title:      "Ruby CLI Data Gem Project"
date:       2018-01-21 03:46:17 +0000
permalink:  ruby_cli_data_gem_project
---


Like many people I was initially intimidated by this project but that slowly changed after watching Avi's Building a CLI Gem Walkthrough. Seeing him go step-by-step from idea to app was tremendously helpful as a project roadmap. I also found reviewing a lot of the past data gem projects to be quite useful as well.

I've always enjoyed playing videogames so I figured a CLI Data Gem for videogame reviews would make sense. I remember how much difficulty I had with the various scraping labs so I spent a fair amount of time looking for a website that would make the scraping process as painless as possible. Surprisingly this turned out to be Metacritic.

Metacritic had by far the most well-structured html that I found with css selectors being both easily identifiable and identical regardless of URL. This made creating the scraper, which was my biggest concern, mercifully quite easy. I did have one issue initially with the scraper and that was the fact it never actually worked thanks to a 403 Forbidden Error. I eventually found out I had to add 'User-Agent' =>'*Browser Name*. Figured I'd include that in case anyone has the same issue.

```
  def scraper
   game_list = Nokogiri::HTML(open(self.url, 'User-Agent' => 'Chrome'))
   
    game_list.css("ol.list_products li.game_product").each do |game|

      @@games << ConsoleReviews::Reviews.new({
        :title => game.css("div.product_title a").text.strip,
        :metascore => game.css("div.metascore_w").text,
        :release_date => game.css("li.release_date span.data").text,
        :link => 'http://www.metacritic.com/' + 
          game.css("div.product_title a").attribute("href").text
      })
    end
  end
```




```
/usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:359:in `open_http': 403 Forbidden (OpenURI::HTTPError)
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:737:in `buffer_open'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:212:in `block in open_loop'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:210:in `catch'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:210:in `open_loop'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:151:in `open_uri'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:717:in `open'
        from /usr/local/rvm/rubies/ruby-2.3.3/lib/ruby/2.3.0/open-uri.rb:35:in `open'
        from /home/ubuntu/workspace/console-reviews/lib/console_reviews/scraper.rb:22:in `scraper'
        from /home/ubuntu/workspace/console-reviews/lib/console_reviews/cli.rb:23:in `list'
        from /home/ubuntu/workspace/console-reviews/lib/console_reviews/cli.rb:58:in `start'
        from /home/ubuntu/workspace/console-reviews/lib/console_reviews/cli.rb:30:in `call'
        from bin/reviews:4:in `<main>'
```

