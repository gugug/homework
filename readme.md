__author__ = 'gu'
f = open(r'/home/gu/PycharmProjects/untitled/trainingset.txt')
list=f.readlines()
if False:
    print list
    m=len(list)
    for i in range(m):
        list[i]=list[i].strip().split(",")
    print list
    print list[0]
    print list[0][0]
a=[]
x1=[]
x2=[]
y=[]
m=len(list)
for i in range(m):
    list[i]=list[i].strip().split(",")
    x1.append(int(list[i][0]))
    x2.append(int(list[i][1]))
    y.append(int(list[i][2]))

if False:
    print x1
    print x2
    print y
sum1=sum(x1)
sum2=sum(x2)
#sum1,sum2=float(sum(x1)),float(sum(x2))
max1,max2=max(x1),max(x2)

min1,min2=min(x1),min(x2)
equallyx1=sum1/m
equallyx2=sum2/m
for i in range(m):
    x1[i]=(x1[i]-equallyx1)/(max1-min1)
    x2[i]=(x2[i]-equallyx2)/(max2-min2)

theta0,theta1,theta2=1.0,2.0,3.0
error=200000000
R=float(raw_input("input your Learning Rate:"))
for i in range(m):
    a=[]
    a[i]=(theta0+theta1*x1[i]+theta2*x1[i]-y[i])*(theta0+theta1*x1[i]+theta2*x1[i]-y[i])
J=sum(a)/(2*m)

while(J>error):
    K=J
    J=0.0
    a,b,c=0.0,0.0,0.0
    a=a+((theta0+x1[i]*theta1+x2[i]*theta2)-y[i])/m
    b=b+((theta0+x1[i]*theta1+x2[i]*theta2)-y[i])*x1[i]/m
    c=c+((theta0+x1[i]*theta1+x2[i]*theta2)-y[i])*x2[i]/m
    theta0=theta0-R*a
    theta1=theta1-R*b
    theta2=theta2-R*c
    for i in range(m):
        a=[]
        a[i]=(theta0+theta1*x1[i]+theta2*x1[i]-y[i])*(theta0+theta1*x1[i]+theta2*x1[i]-y[i])
    J=sum(a)/(2*m)
    if(K<J):R=R/2
print 'Cost Function:'+str(J)







