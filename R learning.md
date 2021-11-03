# R-
R learning 
x <- "amin"
class(x)


x <- as.integer(x)


y <- 236
class(y)

d <- c("ali" , "amin" , "sara")
d4 <- 1:20
print(d4)


d5 <- seq(1,10 , by = 2)
print(d5)

c <- rep(1,5)
print(c)

d6 <- rep(1:3 , 10)
sort(d6 ,decreasing = TRUE)

sort(d6 ,decreasing = FALSE)


sqrt(y)


t <- 10.55
round(t)

max(d6)
min(d6)

#line by line number matrix
A <- matrix(c(1:6) , nrow = 2 , ncol = 3 , byrow = TRUE) 
print(A)

#coloumns number matrix
A <- matrix(c(1:6) , nrow = 2 , ncol = 3 , byrow = FALSE) 
print(A)

dim(A)

A[A %% 2 == 0]
A[A %% 3 == 0]

list(1 , "a" , FALSE , 1+4i , c(1,2,3))

#Data Format
#We must have three vectors of equal length 

products <- c("p1" , "p2" , "p3")
unitprice <- c(20 , 15 , 40)
monthlydemand <- c(1500 , 2000 , 850)
df <- data.frame(products , unitprice , monthlydemand)
print(df)

#input numbers & input string
scan()
scan(what = "")

#one programing saye what s your name & age 
my.neame <- readLines(prompt =" ")
my.age <- readLines(prompt = " ")
print( "hi", my.neame ,"how are you " , my.age+1 , "year old")

#read xlsx file 
#install readxl
#librery readxl
data <- read_excel("D:/ML/Table_S1.xlsx")
View(data)

#missing value
is.na(data$...3)
is.na(data$...6)
sum(is.na(data$...5)
sum(is.na(data$...3)
#########################################
x <- rnorm(200 , mean = 0.8)
cond <- sample(c("A","B"), replace = T , 200)
d - data.frame(cond,x)
head(d)

ggplot(d , aes(x)) + geom_histogram()

ggplot(d , aes(x)) +
  geom_histogram(binwidth = 0.25 , color = "black", fill ="white")

ggplot(d, aes(x)) + geom_density()
ggplot(d , aes(x)) +
  geom_histogram(aes(y=...density...) , binwidth = 0.25 , color = "black" , fill = "white") +
  geom_vline(aes(xintercept = mean(x)) , color = "red" , size = 1.5 , linetype = "dashed")
  geom_density(alpha = 0.2 , fill = "red")
  
  install.packages("shiny")
  library(shiny)
runExample("01_hello")  






#Building the Table Output

ui <- fluidPage(titlePanel("MTCARS Dashboard"),
                sidebarLayout(
                  sidebarPanel(h2("Input"), 
                               sliderInput("mpg", "MPG", min = 10, max = 35, step = 1, round = TRUE, value = 20),
                               radioButtons("gears", "# of Gears",choices = c(3,4,5), selected = 3),
                               selectInput("vs", "VS Type",choices = c(0,1))),
                  mainPanel(
                    h2("Output"),
                    plotOutput("plot"),
                    br(),br(),
                    tableOutput("results")
                  )
                ))
server <- function(input, output) {
  output$plot <- renderPlot({
    
    filtered_data <- mtcars[mtcars$mpg <= input$mpg &
                              mtcars$gear == input$gears &
                              mtcars$vs == input$vs,]
    
    ggplot(data = filtered_data, aes(x = wt, y = mpg)) +
      geom_point()
  })
  output$results <- renderTable({
    
    filtered_data <- mtcars[mtcars$mpg <= input$mpg &
                              mtcars$gear == input$gears &
                              mtcars$vs == input$vs,]
    
    filtered_data
  })
}
shinyApp(ui = ui, server = server)

