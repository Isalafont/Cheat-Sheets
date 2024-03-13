
[Cheatsheet](https://www.reddit.com/r/rails/comments/10a1fww/jsonb_queries_cheatsheet/)
[Gist github Original Post](https://gist.github.com/mabenson00/e64068cd0f6e3f61d59fd30948a9a655)

```ruby
# Basic key operators to query the JSON objects :

# #> : Get the JSON object at that path (if you need to do something fancy)
# -> : Get the JSON object at that path (if you don't)
# ->> : Get the JSON object at that path as text
# {obj, n} : Get the nth item in that object

# https://www.postgresql.org/docs/9.4/functions-json.html#FUNCTIONS-JSONB-OP-TABLE
# Date
# date before today
Segment.where("(data -> ? ->> 'value')::timestamp <= ?", tile[:field], Date.today)

# NESTED VALUE NOT NULL
Segment.where("data -> 'complaint_start_date' ->> 'value' = '2022-10-18'")

# Array Includes X or Y, string
Segment.where("data->'status'->'options' ?\| array[:options]", options: ["open", "closed"]

# Array Includes Integer
Segment.where("data->'approvers'->'ids' @> :value::text::jsonb", value: [@user_id])

#payload: [{"kind"=>"person"}]
Segment.where("payload @> ?", [{kind: "person"}].to_json)

#data: {"interest"=>["music", "movies", "programming"]}
Segment.where("data @> ?", {"interest": ["music", "movies", "programming"]}.to_json)
Segment.where("data #>> '{interest, 1}' = 'movies' ")
Segment.where("jsonb_array_length(data->'interest') > 1")
Segment.where("data->'interest' ? :value", value: "movies")
Segment.where("data -> 'interest' ? :value", value: ['programming'])

# data: {"customers"=>[{:name=>"david"}]}
Segment.where("data #> '{customers,0}' ->> 'name' = 'david' ")
Segment.where("data @> ?", {"customers": [{"name": "david"}]}.to_json)
Segment.where("data -> 'customers' @> '[{\"name\": \"david\"}]'")
Segment.where(" data -> 'customers' @> ?", [{name: "david"}].to_json)

#data: {"uid"=>"5", "blog"=>"recode"}
Segment.where("data @> ?", {uid: '5'}.to_json)
Segment.where("data ->> 'blog' = 'recode'")
Segment.where("data ->> 'blog' = ?", "recode")
Segment.where("data ? :key", :key => 'uid')
Segment.where("data -> :key LIKE :value", :key => 'blog', :value => "%recode%")


# Look up text values in array
#data: {"topic"=>{"options"=>["discrimination"]}, "status"=>{"options"=>["open"]}}
Segment.where("data->'status'->'options' ? :value", value: "open")

#tags: ["dele, jones", "solomon"]
# get a single tag
Segment.where("'solomon' = ANY (tags)")
# which segments are tagged with 'solomon'
Segment.where('? = ANY (tags)', 'solomon')
# which segments are not tagged with 'solomon'
Segment.where('? != ALL (tags)', 'solomon')
# or
Segment.where('NOT (? = ANY (tags))', 'solomon')
#multiple tags
Segment.where("tags @> ARRAY[?]::varchar[]", ["dele, jones", "solomon"])
# tags with 3 items
Segment.where("array_length(tags, 1) >= 3")

# SUM (Thanks @skplunkerin)
#data: [{"amount"=>12.0},{"amount"=>25.50},{"amount"=>17.99}]
Segment.select("SUM((data ->> 'amount')::FLOAT) AS total_amount")
```
