# README

"Create a Basic API with Ruby on Rails - Part 1 - Returning JSON Data" video by webcrunch on YouTube

https://www.youtube.com/watch?v=3S9fyfmCf1A

rails new bands_api --api

code bands_api

rails g scaffold Band name

rails db:migrate

rails s

go to localhost:3000/bands

rails c

Band.create(name: "SYL")

Band.create(name: "ACDC")

Band.create(name: "Rush")

Band.create(name: "Metallica")

Band.create(name: "The Beach Boys")

exit

rails s

Ctrl C

rails g model Member band:references name

rails db:migrate

app/models/band.rb
has_many :members

rails c

bands_controller.rb
adding this to index to show just bands and members in browser without timestamps
include(:members), only: [:name]

Member.create(name: "Angus Young", band_id: 2)

Active Model Serializers provides a way of creating custom JSON in an object-oriented manner.
gem "active_model_serializers"

bundle i

rails g serializer band

app/serializers/band_serializer.rb
add :name
has_many :members

rails g serializer Member
add :name
belongs_to :band

rails c or reload!

Member.create(name: "Devon Townsend", band_id: 1)

Member.create(name: "That One Guy", band_id: 5)

Member.create(name: "Not The Edge", band_id: 4)

Member.create(name: "Canadian Dude", band_id: 3)

Member.create(name: "Not Slash", band_id: 5)

Member.create(name: "Not Mick Jagger", band_id: 2)

adding an initilizer to add JSON "format" for showing the data in a certain form

add a file to initializers
we called it app/cofig/initializers/active_model_serializer.rb

restart server

up next: 
"Create a Basic API with Ruby on Rails - Part 2 - Routing and Versioning" by webcrunch on YouTube
https://www.youtube.com/watch?v=MTnqWxr6djE
