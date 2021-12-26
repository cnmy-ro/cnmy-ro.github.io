# Personal Website
 
Based on the [Jekyll](https://jekyllrb.com/) theme [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes).



--------------
## Development
To test the website locally, run `bundle exec jekyll serve`. The page will be served at `http://localhost:4000//
`.

For more information, check [GitHub Pages and Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)



------------------
## Editing content

- The 4 overview pages are stored in the `_pages` directory.

- Artwork pages are stored as a collection. They're stored in the `_artwork` directory. The actual image files are stored in `/assets/images/artwork_images`.

- Professional pages are stored in `_pages` to keep the projects and publications dirs together. If these 2 were to be made separate collections, they'd result in the case of including 2 collections in the `professional-overview` page, which is tricky.

- Open-source projects pages too are stored in `_pages` for the same reason. 

- Inserting images in any page or post: 
	```html
	<figure class="full">
	    <a href="/assets/images/artwork_images/game_of_life.png">
	    	<img src="/assets/images/artwork_images/game_of_life.png" style="width:100%"></a>
	</figure>
	```



-------
## TODO

- Add actual content

- Remove the search button on the mast. Or figure out how to add search functionality and make the button useful
