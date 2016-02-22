# Graficas-de-Pie-y-Barra
##importar
install.packages("foreign")
library(foreign)
require(foreign)
sociodemo<-read.dbf("C:\\Users\\SALA-C14\\Desktop\\SDEMT315.dbf")
table(sociodemo$CD_A)
table(sociodemo$CLASE1)
#=! diferente 
sociodemo$R_DEF1<-as.numeric(as.character((sociodemo$R_DEF))) #para convertir de numerica a caracter
sociodemo$C_RES1<-as.numeric(as.character((sociodemo$C_RES))) #para convertir de numerica a caracter
sociodemo$EDA1<-as.numeric(as.character((sociodemo$EDA))) #para convertir de numerica a caracter
precod<-subset(sociodemo,((R_DEF1==0) & (C_RES==1 | C_RES==3) & (EDA1>=15 & EDA1<=98)),select = c(EDA1,SEX,HRSOCUP,CLASE2,CLASE1,CLASE3)) #: R_DEF=00 Y C_RES=1 ó 3 y EDAD 14 a 98 AÑOS
precod
table(precod$R_DEF1)
table(precod$C_RES1)
table(precod$EDA1)
attach(precod) #para mandar a llamar la base
CLASEV1<- table(CLASE2)
CLASEV1
hist(CLASE2,)
hist(CLASE2, main="Grafica 1.Distribucion de la poblacion de 15 años o mas, 2015",xlab="Tipo de ocupada",ylab="Poblacion(miles)",xlim=c(0,2),ylim=c(0,200000),border=T,pch=5,col = "mediumpurple1")
memory.size()
sd<-read.dbf("C:\\Users\\SALA-C14\\Desktop\\SDEMT315.dbf")
View(sd)
sd$SEX
sd$CLASE2V<-as.numeric(as.character(sd$CLASE2))#la variable numerica se convierte a caracter
#hacemos unja base solo con las variables seleccionadas
sd1<-subset(sd,CLASE2==1,select=c(EDA,SEX,HRSOCUP,CLASE2,CLASE1,CLASE3,EDA5C,IMSSISSSTE))
frec<-table(sd1$IMSSISSSTE)
frec

#grafica pie
pie(frec)
#labels le ponemos la etiqueta debe de ser vector
pie(frec,labels=c("IMSS","ISSSTE","Otra","No recibe","No especificado"))
#main para poner el titulo
pie(frec,labels=c("IMSS","ISSSTE","Otra","No recibe","No especificado"),
    main = "Institución de atención medica")
pie(frec,labels=c("IMSS","ISSSTE","Otra","No recibe","No especificado"),
    main = "Institución de atención medica")
#col para poner color a cada sector en este caso es un vector
pie(frec,labels=c("IMSS","ISSSTE","Otra","No recibe","No especificado"),
    main="Institución de atención medica",col = c("green","red","blue","gray","yellow"))

#grafica de barras
#sacamos las frecuencias de las variables a utilizar
frec1<-table(sd1$EDA5C)
View(frec1)
#ponemos titulo
barplot(frec1,main="Gráfica 1. Cinco grupos de edad", col=c("green","red","blue","gray","yellow","brown"),names.arg = c("menor","14 a 24","25 a 44","45 a 64","65 y más","n.e"),xlab = "Edad",ylab = "Población",ylim = c(0,150000))
memory.size() #para definir cuanta memoria va a usar R
