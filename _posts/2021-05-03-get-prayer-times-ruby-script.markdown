---
layout: post
title:  "Get prayer times with ruby(athan api)"
date:   2021-05-03 08:20:00 +0100
categories: rspec ruby rails
---

```ruby

require 'uri'
require 'net/http'
require 'json'

country = 'Morocco'
city = 'Tangier'

uri = URI("http://api.aladhan.com/v1/timingsByCity?city=#{city}&country=#{country}&method=8")
response = Net::HTTP.get_response(uri)
data = JSON.parse response.body

gregorian_date =  data.dig('data', 'date', 'readable')
hijri_date =  data.dig('data', 'date', 'hijri', 'date')
timing_hash = data.dig('data', 'timings')

puts "Date: #{hijri_date} - #{gregorian_date}"
timing_hash.each do |key, value|
  puts '-----------------'
  puts "#{key} : #{value}"
end

```