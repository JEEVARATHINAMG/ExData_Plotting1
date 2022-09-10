###  plot1.R

f<-read.table("household_power_consumption.txt", header = T,
               sep=";", comment.char="%", stringsAsFactors=FALSE, na.strings="?")
dim(df)
dataplott<- subset(df,df$Date=="1/2/2007"|df$Date=="2/2/2007")
datetime <- strptime(paste(dataplott$Date, dataplott$Time, sep=" "), "%d/%m/%Y %H:%M:%S")
plot1 <- function() {
  hist(dataplott$Global_active_power,col="red",xlab="Global Active Power(kilowatts)",
       main="Global Active Power")
  dev.copy(png, file="plot1.png", width=480, height=480)
  dev.off()
}
plot1()

### plot2.R
plot2 <- function() {
  plot(datetime,dataplott$Global_active_power,ylab="Global Active Power(kilowatts)",
       xlab="",type="l")
  dev.copy(png, file="plot2.png", width=480, height=480)
  dev.off()
}
plot2()

### plot3.R 
plot3 <- function() {
  plot(datetime,dataplott$Sub_metering_1,type="n",xlab = "",ylab="Energy sub metering")
  lines(datetime,dataplott$Sub_metering_1,col="black")
  lines(datetime,dataplott$Sub_metering_2,col="red")
  lines(datetime,dataplott$Sub_metering_3,col="blue")
  legend("topright",lty=c(1,1,1),col=c("black","red","blue"),legend=c("Sub_meeting_1","Sub_meeting_2"
                                                                      ,"Sub_meeting_3"))
  dev.copy(png, file="plot3.png", width=480, height=480)
  dev.off()
}
plot3()

### plot4.R
par(mfrow=c(2,2))
plot4<-function(){
  plot(datetime,dataplott$Global_active_power,ylab="Global Active Power",
       xlab="",type="l")
  plot(datetime,dataplott$Voltage,ylab="Voltage",type="l")
  plot(datetime,dataplott$Sub_metering_1,type="n",xlab = "",ylab="Energy sub metering")
  lines(datetime,dataplott$Sub_metering_1,col="black")
  lines(datetime,dataplott$Sub_metering_2,col="red")
  lines(datetime,dataplott$Sub_metering_3,col="blue")
  legend("topright",lty=c(1,1,1),col=c("black","red","blue"),legend=c("Sub_meeting_1","Sub_meeting_2"
                                                                      ,"Sub_meeting_3"))
  plot(datetime,dataplott$Global_reactive_power,type="l",ylab="Global_reactive_power")
  dev.copy(png, file="plot4.png", width=480, height=480)
  dev.off()
}
plot4()



###![plot1](https://user-images.githubusercontent.com/109571969/189503484-ac3c6e2a-505d-4cc9-88d4-ae36914ae443.png)
![plot1](https://user-images.githubusercontent.com/109571969/189503497-0bad9a45-649d-4ec0-aa05-2585d0a0657c.png)
![plot2](https://user-images.githubusercontent.com/109571969/189503503-9289af90-427c-4fa6-b16a-be350b7b0256.png)
![plot3](https://user-images.githubusercontent.com/109571969/189503508-92c5c795-c1cd-4898-9db2-54f859aa0f96.png)
![plot4](https://user-images.githubusercontent.com/109571969/189503513-cdedfa67-2a75-4558-8762-7e975c374067.png)
### ![plot1](https://user-images.githubusercontent.com/109571969/189503536-b06d349f-5f5c-4112-8011-c3d980904b45.png)
