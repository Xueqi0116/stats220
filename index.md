## provide the R code I used to make the meme
library(magick)
white_cat <- image_read("https://preview.redd.it/dm4yvdcd11771.jpg?width=360&format=pjpg&auto=webp&s=ddd96212d2b35ede767845b7a26cfac5e6276cda") %>%
  image_scale(500)

brown_bear <- image_read("https://exploringbits.com/wp-content/uploads/2022/01/cute-pfp-4.jpg?ezimgfmt=rs:352x354/rscb3/ng:webp/ngcb3") %>%
  image_scale(500)

cute_panda <- image_read("https://thumbs.dreamstime.com/b/cute-panda-animal-cartoon-character-hugging-love-heart-illustration-213323480.jpg") %>%
  image_scale(500)

yummy_text <- image_blank(width = 500, 
                          height = 500, 
                          color = "#000000") %>%
  image_annotate(text = "Yummy!",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

bubble_text <- image_blank(width = 500, 
                         height = 500, 
                         color = "#000000") %>%
  image_annotate(text = "Bubbles!",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

love_text <- image_blank(width = 500, 
                       height = 500, 
                       color = "#000000") %>%
  image_annotate(text = "Hug love!",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

first_row <- c(white_cat, yummy_text) %>%
  image_append()

second_row <- c(brown_bear, bubble_text) %>%
  image_append()

third_row <- c(cute_panda, love_text) %>%
  image_append()

c(first_row, second_row, third_row) %>%
  image_append(stack = TRUE)

image_write(meme, "my_meme.png")
