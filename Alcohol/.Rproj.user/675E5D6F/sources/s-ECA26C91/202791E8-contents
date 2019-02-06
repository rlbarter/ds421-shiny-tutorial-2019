library(shiny)
library(tidyverse)
library(gt)
# load in data 
bcl <- read_csv("bcl-data.csv")


# Define UI for application that draws a histogram
ui <- fluidPage(
  titlePanel("BC Liquor Store prices"),
  sidebarLayout(
    sidebarPanel(
      sliderInput(inputId = "priceInput", 
                  label = "Price", 
                  min = 0, max = 100,
                  value = c(25, 40), pre = "$"),
      radioButtons(inputId = "typeInput", 
                   label = "Product type",
                   choices = c("BEER", "REFRESHMENT", "SPIRITS", "WINE"),
                   selected = "WINE"),
      selectInput("countryInput", "Country",
                  choices = c("CANADA", "FRANCE", "ITALY", "UNITED STATES OF AMERICA", "AUSTRALIA"))
    ),
    mainPanel(
      plotOutput("coolplot"),
      br(), br(),
      tableOutput("results")
    )
  )
)

# Define server logic required to draw a histogram
server <- function(input, output) {
   output$coolplot <- renderPlot({
     bcl %>%
       filter(Country == input$countryInput,
              Type %in% input$typeInput,
              Price >= input$priceInput[1] & Price <= input$priceInput[2]) %>%
       ggplot() +
         geom_histogram(aes(x = Alcohol_Content)) +
         theme_classic()
   })
   
   output$results <- renderTable({
     bcl %>%
       filter(Country == input$countryInput,
              Type %in% input$typeInput,
              Price >= input$priceInput[1] & Price <= input$priceInput[2]) %>%
       gt
   })
}

# Run the application 
shinyApp(ui = ui, server = server)

