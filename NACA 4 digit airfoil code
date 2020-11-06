fprintf('We will do source panel method for NACA 4 digit series of airfoil');
fprintf('Enter the 4 digit NACA series \n');
c = input('Enput the chord length \n');
R = input('Enter the first digit \n');
Q = input('Enter the second digit \n');
KK = input('Enter the last two digits \n');

x = 0:0.0001:1;
if R ==0 && Q ==0
     Symm = 1;
     disp('Symmetric Airfoil')
else
     Symm = 0;
     disp('Cambered Airfoil')
end
if R ==0 && Q ==0
    t = KK/100;
    y_t = 5*t*(0.2969*sqrt(x)-0.126*(x)-0.3516*(x).^2+0.2843*(x).^3-0.1015*(x).^4); 
    y_upper = y_t;
    y_lower = -y_t;
    x_upper = x;
    x_lower = x;
else
    m = R/100;
    p = Q/10;
    t = KK/100;
    m = p*c;
    for i = 1:length(x)
        if x(i)<= m
            f = x(i)/c;
            y_c(i) = (m/p^2)*((2*p*f)-(f^2));
            dy_c(i) = (2*m*(p-f))/p^2;
        else
            f = x(i)/c;
            y_c(i) = (m/((1-p)^2))*((1-2*p)+(2*p*f)-(f^2));
            dy_c(i) = (2*m*(p-f))/((1-p)^2);
        end
    end
    y_t = 5*t*(0.2969*sqrt(x)-0.126*(x)-0.3516*(x).^2+0.2843*(x).^3-0.1015*(x).^4); 
    theta = atan(dy_c);
    x_upper = x-y_t.*sin(theta);
    x_lower = x+y_t.*sin(theta);
    y_upper = y_c+y_t.*cos(theta);
    y_lower = y_c-y_t.*cos(theta);
end
figure
hold on
grid on
axis equal
plot(x_upper,y_upper,x_lower,y_lower,'LineWidth',2,'color','b')
plot(x,y_c,'--','LineWidth',2,'color','r')
title('NACA airfoil')
xlabel('x')
ylabel('y')
    
