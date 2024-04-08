# Data Dinos!
Curious about becoming more versed in dinosaur vocabulary? Don't have the mental capacity to ACTUALLY study dinosaur names but would rather look up cool dinos on your favorite search engine and guess that dinosaur's name... Just use our dino identifier to identify ten of the top twenty dinosaurs out on the interwebs.

## Inspiration
We’ve all been there - reading books about dinosaurs, wondering what kind it is. We know what a T-rex looks like, some of us may know what a Pterodactyl looks like as well. But what about other dinosaurs that are less common – like the Ankylosaurus, or the Stegosaurus? Looking at an image of a dinosaur, we may recognize it from our memory, but it is always a struggle to remember the name of the dinosaur it is. 

## What It Does
This is why we’ve made our own dinosaur classification model to help identify the kind of dinosaur it is from a single image. We’ve collected data on ten of the 20 most popular dinosaurs on the internet (https://www.activewild.com/famous-dinosaurs/), and built a model to be able to label the image by its kind.

## Our Steps of Machine Learning Development
After looking for image datasets, there weren’t that many applicable datasets so we instead decided to web-scrape for images via a Google Extension. We were able to effectively preprocess the data we were made available with with 10 popular dinosaurs (ankylosaurus, deinonychus, dilophosaurus, diplodocus, pterodactyl, spinosaurus, stegosaurus, triceratops, tyrannosaurus-rex, and velociraptor):
We wanted to make our data as uniform as possible by resizing each image in our data into (250, 250) length times width
We then grayscale each image to reduce the dimensionality of the images into one channel (instead of the 3 RGB channels). This allows for easier computation on our training models, allowing quicker training times and lower memory consumption. This also reduces the illumination in images, such as lighting conditions, that are not necessary for training to further improve performance.
Since we’re using PyTorch, we thought it was generally more convenient to convert grayscale images directly into tensors as PyTorch is optimized for tensor operations, and using tensors can simplify your code and make it more compatible

Once the images were collected, it was placed under a Dataset object where we transformed each image by resizing and converting them into tensors. In addition, the dataset was split into training, validation, and testing data loaders so they are easily interpreted by our model. For our model selection, we decided to go with the built-in resnet50 model. Next, we trained the model under 5 epochs and kept track of our loss as measured by cross-entropy. When finished training, we calculated various metrics such as our accuracies and running loss.  

## Challenges we ran into
A challenge we ran into was having limited valid and “real” images of dinosaurs which are not just fossils or cartoon drawings. First and foremost, granted that our machine learning project revolved around small data of dinosaurs, we decided to webscrape our own images in hopes of garnering more data via a Google Extension. Even then, our initial cleaning after web scraping took out a lot of the raw data we were working with as a decent amount of the images we removed were not particularly related to the respective dinosaur species. As obvious as it is, this already causes potential problems for the rest of our project. This made our machine learning model harder to optimize, even with the pre-trained model, and with the time constraint, we also didn’t have enough time to fine-tune the parameters of our pre-trained models and even play with more models. In addition, we didn’t have much time to explore testing other models, running more epochs, and trying out various layer weights. Another

## Accomplishments that we're proud of
Considering we have limited experience in deep learning, we are proud that we could navigate our way through uncharted territory. By testing our technical knowledge through creating an image classifier in PyTorch, we were able to adapt, learn new techniques, and create an impressive project.

## What we learned
The most important aspect we learned was how important the data was in order to optimize the accuracy of our model. We discovered that the accuracy depends on a variety of factors including the number of epochs, learning rate, and the batch size, but most importantly on the data we train it with. 

## What's next for Dino Identifier
   ### Combining Notebooks
In our repository, we have two notebooks which we worked on. The datadinoanalysis.ipynb serves as the main notebook for this project, and the data-dino-analysisv2.ipynb notebook was one we worked on mainly for the preprocessing of the data. For our next steps, we would love to combine these two notebooks together, as the more detailed preprocessing could potentially allow for better data to be used for our model. After this implementation, we would also love to add another testing feature, where we can use our trained model to predict individual images that we input to label for the kind of dinosaur.

   ### More Cohesive Web Scraper
Granted our small dataset, we could make a more cohesive web scraper using Python, HTML, and BeautifulSoup to garner much more data. Although there are no guarantees that our data will be substantially bigger; hopefully it’s enough to use for our machine learning model.

   ### Data Augmentation
Alternatively, instead of solely relying on a web scraper to increase our dataset size, we can also augment our existing dataset by applying transformations such as rotation, scaling, and flipping to the images, helping us create additional training samples and improve the model’s ability to classify these images more generally.

   ### Tuning
Maybe with a larger time constraint, we could also play along with the different pre-trained models during transfer learning. Given the pre-trained models we can use at our disposal in PyTorch (and any other Deep Learning library), we can also try various parameters and/or manually tune our parameters to better figure out optimization. This also includes fine-tuning pre-trained models and hyperparameter tuning.