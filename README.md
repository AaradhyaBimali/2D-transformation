# 2D-transformation scaling and translation
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the display
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Bresenham Algorithm") #set exe header

# Colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

def translate(tx,ty,x1,y1,x2,y2):
    x1=x1+tx
    y1=y1+ty
    x2=x2+tx
    y2=y2+ty
    bresen(x1,y1,x2,y2)

def scale(x1,y1,x2,y2,sx,sy):
    x1=x1*sx
    x2=x2*sx
    y1=y1*sy
    y2=y2*sy
    bresen(x1,y1,x2,y2)
    
def bresen(x1,y1,x2,y2):
    dx=x2-x1
    dy=y2-y1
    if(x2>x1):
        lx=1
    else:
        lx=-1
    if(y2>y1):
        ly=1
    else:
        ly=-1
    k=0
    if (dx>dy):
        P=2*dy-dx
        while(k<dx):
            
            if (P<0):
                x1=x1+lx
                y1=y1
                P=P+2*dy
                
                screen.set_at((x1,y1), WHITE)
            else:
                x1=x1+lx
                y1=y1+ly
                P=P+2*(dy-dx)
                screen.set_at((x1,y1), WHITE)
            k=k+1
    else:
        P=2*dx-dy
        while(k<dy):
            screen.set_at((x1,y1), WHITE)
            
            if (P<0):
                x1=x1
                y1=y1+ly
                P=P+2*dx
            else:
                x1=x1+lx
                y1=y1+ly
                P=P+2*(dx-dy)
            k=k+1
                

def main():
    while True:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()

        # Clear the screen
        screen.fill(BLACK)
        translate(250,250,100,250,200,70)
        bresen(100,250,200,70)
        scale(100,250,200,70,2,2)
        
    
        
        #bresen()
# Update the display
        pygame.display.flip()


if __name__ == "__main__":
    main()
        
        
        
