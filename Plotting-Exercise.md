## Plotting Assignment 1 for Exploratory Data Analysis
### Instructions
This assignment uses the data from [UC Irvine Machine Learning Repository] (http://archive.ics.uci.edu/ml/index.php). Particular data
to be worked on is the [Electric power consumption] (https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip).

### downloading and reading the data
     url <- "http://archive.ics.uci.edu/ml/machine-learning-databases/00235/household_power_consumption.zip"
     dat <- download.file(url,destfile = "data.zip")
     #Unzip the data to remain with the   "household_power_consumption.txt"
     unzip("data.zip")
     
     #Read the data into R
     data <- read.table("household_power_consumption.txt", header = TRUE, sep = ";", na.strings = "?", colClasses = c('character', 
     'character', rep('numeric', 7))
     
     #Format the Date column of the data
     data$Date <- as.Date(t$Date, "%d/%m/%Y")
     DAT1 <- as.Date("2007-2-1")
     DAT2 <- as.Date("2007-2-2")
     
     #Subset the data into the dates for consideration
      data <- subset(data, Date >= DAT1 & Date <= DAT2)
      
    #Create a DateTime column
    data$DateTime <- strptime(paste(data$Date, data$Time), "%d/%m/%Y %H:%M:%S"))
    
    #Remove the Date and Time columns
    data <- data[ , !(names(data) %in% c("Date", "Time")))]   
    
    
    #Remove the incomplete cases from data
     data <- data[complete.cases(data),]
     
    #Format the DateTime column
    
    data$DateTime <- as.POSIXct(DateTime)
### Plot 1
     ## Create the histogram
     hist(data$Global_active_power, main="Global Active Power", xlab = "Global Active Power (kilowatts)", col="red") 
![alt text](https://github.com/otienodominic/ExData_Plotting1/blob/master/plot1.png?raw=true)
     
### Plot 2
      ## Create Plot 2
      plot(data$Global_active_power~t$dateTime, type="l", ylab="Global Active Power (kilowatts)", xlab="")
![alt text](https://github.com/otienodominic/ExData_Plotting1/blob/master/plot2.png?raw=true)

### Plot 3
      #Create Plot 3
      with(data, {
        plot(Sub_metering_1~dateTime, type="l",
             ylab="Global Active Power (kilowatts)", xlab="")
        lines(Sub_metering_2~dateTime,col='Red')
        lines(Sub_metering_3~dateTime,col='Blue')
      })
      legend("topright", col=c("black", "red", "blue"), lwd=c(1,1,1), 
     c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))
![alt text](https://github.com/otienodominic/ExData_Plotting1/blob/master/plot3.png?raw=true)

### Plot 4
          ## Create Plot 4
    par(mfrow=c(2,2), mar=c(4,4,2,1), oma=c(0,0,2,0))
    with(data, {
      plot(Global_active_power~dateTime, type="l", 
           ylab="Global Active Power (kilowatts)", xlab="")
      plot(Voltage~dateTime, type="l", 
           ylab="Voltage (volt)", xlab="")
      plot(Sub_metering_1~dateTime, type="l", 
           ylab="Global Active Power (kilowatts)", xlab="")
      lines(Sub_metering_2~dateTime,col='Red')
      lines(Sub_metering_3~dateTime,col='Blue')
      legend("topright", col=c("black", "red", "blue"), lty=1, lwd=2, bty="n",
             legend=c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))
      plot(Global_reactive_power~dateTime, type="l", 
           ylab="Global Rective Power (kilowatts)",xlab="")
      })
![alt text](https://github.com/otienodominic/ExData_Plotting1/blob/master/plot4.png?raw=true)
