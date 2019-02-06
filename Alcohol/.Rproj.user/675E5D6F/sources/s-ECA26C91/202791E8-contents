library(shiny)
library(tidyverse)
# load in data 
bcl <- read_csv("bcl-data.csv")


# Define UI for application that draws a histogram
ui <- fluidPage(
  titlePanel("BC Liquor Store prices"),
  sidebarLayout(
    sidebarPanel(
      # slider input
      sliderInput(inputId = "priceInput", 
                  label = "Price", 
                  min = 0, max = 100,
                  value = c(25, 40), pre = "$")
    ),
    mainPanel("the results will go here")
  )
)

# Define server logic required to draw a histogram
server <- function(input, output) {
   
 
}

# Run the application 
shinyApp(ui = ui, server = server)

