$(function() {
  // jQuery goes here...
  var galleryImage = $(".gallery").find("img").first();
  var images = [
  "images/laptop-mobile_small.jpg",
  "images/laptop-on-table_small.jpg",
  "images/people-office-group-team_small.jpg"
  ];
  
 var i=0;
 setInterval(function(){
 	i = (i+1) % iamges.length; //0,1,2,0,1,2
 	galleryImage.fadeOut(function(){
 		$(this).attr("src", images[i]); // $this refers to gallery image
        $(this).fadeIn();
 	});
 	console.log(galleryImage.attr("src"));
 },2000);
});