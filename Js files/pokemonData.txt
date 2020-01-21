$(function() {
  
  var pokeapiUrl = "https://pokeapi.co/api/v2/generation/1";

  $.getJSON(pokeapiUrl).done(function(data){
   console.log(data);
   $.each(data.pokemon_species, function(index, pokemon){
   	var name = pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1)// charAt(0)- captalize 1st letter slice(1)-rest without first letter
   	var par = $("<p>").html("Pokemon species no. " + (index+1) + " is " + name);
   	par.appendTo("#pokemon");
   });
  }).fail(function(){
  	console.log("Request to PokeAPI Failed");
  }).always(function(){
  	console.log("Pokemon is awesome");
  });
});

