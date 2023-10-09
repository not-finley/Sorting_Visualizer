# Author Finley Harrison
# This program will create a visual representation of different sorting algorithms, using pygame. The user will be able to start a algorithm by clicking different buttons 
from random import shuffle
import pygame

# For the Merge sort and Quick sort functions 
arr_clr =[(0, 204, 102)]*300
clr =[(0, 204, 102), (255, 0, 0), 
(0, 0, 153), (255, 102, 0)]

# A function that will take a list input and a width input and output a series of bars with their height based of the size of the number, it will also create back and quit buttons 
def show(list1,width1):
    # Gets rid of any previous frames 
    screen.fill((179, 179, 179))
    colour = (225, 225, 225)
    for i in range(len(list1)):
        # If the list is sorted the bars will be coloured with a stronger green the taller the bar
        if (list1 == sorted(list1)):
            if list1[i]+50 > 255:
                colour = (0, 255,50)
            else:
                colour = (0,list1[i]+50,50)
        # If the list isn't sorted the bars will be coloured a amount of blue based on their height 
        else:
            if list1[i]+50 >= 255:
                colour = (0,200,255)
            else:
                colour = (0,list1[i],list1[i]+50)
        # Draws a rectangle for each item in the list with the colour and the height based on the number of that item in the list
        pygame.draw.rect(screen, colour,(35 + ((width1 - .5 ) * i), 500 - (list1[i]), width1, (list1[i])))
    # Gets the mouse position
    mouse = pygame.mouse.get_pos()
    for ev in pygame.event.get():
        # If the mouse is clicked and over either the back or quit button
        if ev.type == pygame.MOUSEBUTTONDOWN:
            if (width / 2) + 130 <= mouse[0] <= width / 2 + 270 and height / 2 - 200 <= mouse[1] <= height / 2 - 160:
                pygame.quit()
            if (width / 2) - 275 <= mouse[0] <= width / 2 - 135 and height / 2 - 200 <= mouse[1] <= height / 2 - 160:
                return False

    if (width / 2) + 130 <= mouse[0] <= (width /2) + 270 and height / 2 - 200 <= mouse[1] <= height / 2 - 160:
        pygame.draw.rect(screen, ((56, 56, 56)),[(width / 2) + 130, height / 2 - 200, 140, 40])
    else:
        pygame.draw.rect(screen, ((109, 112, 108)),[(width / 2) + 130, height / 2 - 200, 140, 40])

    if (width / 2) - 275 <= mouse[0] <= (width /2) - 135 and height / 2 - 200 <= mouse[1] <= height / 2 - 160:
        pygame.draw.rect(screen, ((56, 56, 56)),[(width / 2) - 275, height / 2 - 200, 140, 40])
    else:
        pygame.draw.rect(screen, ((109, 112, 108)),[(width / 2) - 275, height / 2 - 200, 140, 40])

    screen.blit(quit, ((width / 2) + 200 - (quit_width / 2),(height / 2) - 200 + (quit_height / 3)))
    screen.blit(back_text, ((width / 2) - 200 - (back_width / 2),(height / 2) - 200 + (back_height / 3)))
    pygame.display.update()

# This function checks if the input list is sorted if it is it ends and if it is not it shuffles the list 
def bogo_sort(list1,width):
    is_sorted = False
    # While the list is not sorted the list getts shuffled 
    while is_sorted == False:
        shuffle(list1)
        x = show(list1,width)
        if x == False:
            return False
            break
        if (list1 == sorted(list1)):
            is_sorted = True
    return list1

# Takes a input list for every item in that list it checks if the items above it are less then it if they are it moves the selected item up untill the list is sorted
def bubble_sort(list1,width):
    n = len(list1)

    for i in range(n):
        already_sorted = True
        for j in range(n - i - 1):

            if list1[j] > list1[j + 1]:
                list1[j], list1[j + 1] = list1[j + 1], list1[j]
            x = show(list1,width)
            if x == False:
                return False
                break
            already_sorted = False

        if already_sorted:
            break

    return list1

# goes through the list one item at a time if 
def insertion_sort(list1,width):
    for i in range(1, len(list1)):

        key_item = list1[i]

        j = i - 1

        while j >= 0 and list1[j] > key_item:
            list1[j + 1] = list1[j]
            j -= 1
            x = show(list1, width)
            if x == False:
                return False
        list1[j + 1] = key_item
    return list1


def selection_sort(list1,width):
    for i in range(len(list1)):
        min_idx = i
        for j in range (i+1, len(list1)):
            if list1[min_idx] > list1[j]:
                min_idx = j
        list1[i], list1[min_idx] = list1[min_idx], list1[i]
        x = show(list1, width)
        if x == False:
            return False
            break
        pygame.time.delay(20)
    return list1


# I got help from someone elses code for the merge sort algorithm as it uses recursion 
# https://www.geeksforgeeks.org/sorting-algorithm-visualization-merge-sort/
def mergesort(list1,l,r,width):
    mid =(l + r)//2
    if l<r:
        y = mergesort(list1, l, mid, width)
        if y == False:
            return False
        s = mergesort(list1, mid + 1, r, width)
        if s == False:
            return False
        x = merge(list1, l, mid,mid + 1, r, width)
        if x == False:
            return False


def merge(list1,x1,y1,x2,y2,width):
    i = x1
    j = x2
    temp =[]
    pygame.event.pump() 
    while i<= y1 and j<= y2:
        arr_clr[i]= clr[1]
        arr_clr[j]= clr[1]
        x = show(list1,width)
        if x == False:
            return False
            break
        arr_clr[i]= clr[0]
        arr_clr[j]= clr[0]
        if list1[i]<list1[j]:
                temp.append(list1[i])
                i+= 1
        else:
                temp.append(list1[j])
                j+= 1
    while i<= y1:
        arr_clr[i]= clr[1]
        x = show(list1,width)
        if x == False:
            return False
            break
        arr_clr[i]= clr[0]
        temp.append(list1[i])
        i+= 1
    while j<= y2:
        arr_clr[j]= clr[1]
        x = show(list1,width)
        if x == False:
            return False
            break
        arr_clr[j]= clr[0]
        temp.append(list1[j])
        j+= 1
    j = 0    
    for i in range(x1, y2 + 1): 
        pygame.event.pump() 
        list1[i]= temp[j]
        j+= 1
        arr_clr[i]= clr[2]
        x = show(list1,width)
        if x == False:
            return False
            break
        if y2-x1 == len(list1)-2:
            arr_clr[i]= clr[3]
        else: 
            arr_clr[i]= clr[0]


# Quick sort Functions
def quicksort(list1,l,r,width):
    if l<r:
        pi = partition(list1, l, r, width)
        if pi == "x":
            return False
        i = quicksort(list1, l, pi-1, width)
        if i == False:
            return False
        d = show(list1,width)
        if d == False:
            return False
        for i in range(0, pi + 1):
            arr_clr[i]= clr[3]
        e = quicksort(list1, pi + 1, r, width)
        if e == False:
            return False
            


def partition(list1,low,high,width):
    pygame.event.pump() 
    pivot = list1[high]
    arr_clr[high]= clr[2]
    i = low-1
    for j in range(low, high):
        arr_clr[j]= clr[1]
        x = show(list1,width)
        if x == False:
            return "x"
        arr_clr[high]= clr[2]
        arr_clr[j]= clr[0]
        arr_clr[i]= clr[0]
        if list1[j]<pivot:
            i = i + 1
            arr_clr[i]= clr[1]
            list1[i], list1[j]= list1[j], list1[i]
    y = show(list1,width)
    if y == False:
        return False
    arr_clr[i]= clr[0]
    arr_clr[high]= clr[0]
    list1[i + 1], list1[high] = list1[high], list1[i + 1] 
      
    return ( i + 1 )


pygame.init()

# A function that is given a y and x input for the top left corner of a button, if the button is hovered over then the button changes colour 
def draw_button(x,y):
    if x  <= mouse[0] <= x + 140 and y <= mouse[1] <= y + 40:
        pygame.draw.rect(screen, ((56, 56, 56)),[x, y, 140, 40])
    else:
        pygame.draw.rect(screen, ((109, 112, 108)),[x, y, 140, 40])


diff_list = [1,2,3,6,12,30,60]
bar_width_list = [2,4,6,11,22,53,105]
index = 1

list_length = 300
bar_width = 105
diff = 60

width = 600
height = 500

smallfont = pygame.font.SysFont('Corbel', 35)
text1 = smallfont.render('Selection', True, (225, 225, 225))
text2 = smallfont.render('Insertion', True, (225, 225, 225))
text3 = smallfont.render('Bubble', True, (225, 225, 225))
text4 = smallfont.render('Bogo', True, (225, 225, 225))
text5 = smallfont.render('Merge', True, (225, 225, 225))
text6 = smallfont.render('Quick', True, (255, 255, 255))

quit = smallfont.render('Quit', True, (225, 225, 225))
back_text = smallfont.render('Back', True, (225, 225, 225))

text_width1, text_height1 = smallfont.size("Selection")
text_width2, text_height2 = smallfont.size("Insertion")
text_width3, text_height3 = smallfont.size("Bubble")
text_width4, text_height4 = smallfont.size("Bogo")
text_width5, text_height5 = smallfont.size("Merge")
text_width6, text_height6 = smallfont.size("Quick")

quit_width, quit_height = smallfont.size("Quit")
back_width, back_height = smallfont.size("Back")

screen = pygame.display.set_mode([width, height])


while True:
    sort_type = ""
    pygame.display.set_caption("Sort")
    pygame.display.update()
    # Main Menu
    while True:
        # Gets the mouse position for each frame 
        mouse = pygame.mouse.get_pos()
        # Covers anything that was on screen last frame
        screen.fill((179, 179, 179))
        bar_width = bar_width_list[index]
        diff = diff_list[index]

        for ev in pygame.event.get():
            # Checks if the mouse button is pressed
            if ev.type == pygame.MOUSEBUTTONDOWN:
                # For each button if the mouse is pressed down in that area it assigns the sort_type to the one of the button
                if 230 <= mouse[0] <= 370 and 70-40 <= mouse[1] <= 110-40:
                    sort_type = "Selection Sort"
                if 230 <= mouse[0] <= 370 and 150-40 <= mouse[1] <= 190-40:
                    sort_type = "Insertion Sort"
                if 230 <= mouse[0] <= 370 and 230-40 <= mouse[1] <= 270-40:
                    sort_type = "Bubble Sort"
                if 230 <= mouse[0] <= 370 and 310-40 <= mouse[1] <= 350-40:
                    sort_type = "Bogo Sort"
                if 230 <= mouse[0] <= 370 and 390-40 <= mouse[1] <= 430-40:
                    sort_type = "Merge Sort"
                if 230 <= mouse[0] <= 370 and 470-40 <= mouse[1] <= 510-40:
                    sort_type = "Quick Sort"
            
                # If the mouse clicks on one of the plus or minus buttons and it isn't already at max or min it will change the index accordingly 
                if (width / 2) + 180 <= mouse[0] <= (width / 2) + 220 and height / 2 - 100 <= mouse[1] <= height / 2 -60 and index != 0:
                    index -= 1
                if (width / 2) + 180 <= mouse[0] <= (width / 2) + 220 and height / 2 +30 <= mouse[1] <= height / 2 +70 and index != 6:
                    index += 1
        # Creates a new text based of the index currently
        list_size_text = smallfont.render(str(int(list_length / diff)), True, (56,56,56))    
        list_size_width, list_size_height = smallfont.size(str(int(list_length / diff)))
        # Callse the draw_button Function to make 6 buttons 
        draw_button(230,70-40)
        draw_button(230,150-40)
        draw_button(230,230-40)
        draw_button(230,310-40)
        draw_button(230,390-40)
        draw_button(230,470-40)

        # Creates the plus and minus buttons, If the index is at max on either end the either the plus or minus button will have a lighter colour 
        if (width / 2) + 180 <= mouse[0] <= (width / 2) + 220 and height / 2 - 100 <= mouse[1] <= height / 2 -60 and index != 0:
            pygame.draw.rect(screen, ((56, 56, 56)),[(width / 2) + 180, height / 2 - 100, 40, 40])
        elif index == 0:
            pygame.draw.rect(screen, ((150,150,150)),[(width / 2) + 180, height / 2 - 100, 40, 40])
        else:
            pygame.draw.rect(screen, ((109, 112, 108)),[(width / 2) + 180, height / 2 - 100, 40, 40])

        if (width / 2) + 180 <= mouse[0] <= (width / 2) + 220 and height / 2 +30 <= mouse[1] <= height / 2 +70 and index != 6:
            pygame.draw.rect(screen, ((56, 56, 56)),[(width / 2) + 180, height / 2 + 30, 40, 40])
        elif index == 6:
            pygame.draw.rect(screen, ((150,150,150)),[(width / 2) + 180, height / 2 + 30, 40, 40])
        else:
            pygame.draw.rect(screen, ((109, 112, 108)),[(width / 2) + 180, height / 2 + 30, 40, 40])
        # Draws to screen all the text over the buttons, using the text height and width to center the text 
        screen.blit(text1, (300 - (text_width1 / 2), 70 - 40 + (text_height1 / 3)))
        screen.blit(text2, (300 - (text_width2 / 2), 150 - 40 + (text_height2 / 3)))
        screen.blit(text3, (300 - (text_width3 / 2), 230 - 40 + (text_height3 / 3)))
        screen.blit(text4, (300 - (text_width4 / 2), 310 - 40 + (text_height4 / 3)))
        screen.blit(text5, (300 - (text_width5 / 2), 390 - 40 + (text_height5 / 3)))
        screen.blit(text6, (300 - (text_width6 / 2), 470 - 40 + (text_height6 / 3)))
        screen.blit(list_size_text, ((width / 2)+ 200 - (list_size_width/2),(height / 2) - list_size_height))

        pygame.display.update()
        if sort_type != "":
            break
    # Sets the caption of the window to the sort type chosen    
    pygame.display.set_caption(sort_type)
    # Updates the display
    pygame.display.update()
    # Creates a new list
    list1 = []
    # Generates a list from 1 to the picked list length and then shuffles it 
    for i in range(1,list_length+1, diff):
        list1.append(i)
    shuffle(list1)

    # The sort allgorithm is run based on the sort_type assigned when a sort button was pressed
    # Each function is run and stored in a variable called x, if the back button is pressed while the sort function is running 
    # it will return False so if x is false the main menue is displayed again 

    if sort_type == "Insertion Sort":
        x = insertion_sort(list1,bar_width)
    elif sort_type == "Bubble Sort":
        x = bubble_sort(list1,bar_width)
    elif sort_type == "Bogo Sort":
        x = bogo_sort(list1,bar_width)
    elif sort_type == "Selection Sort":
        x = selection_sort(list1,bar_width)
    elif sort_type == "Merge Sort":
        x =  mergesort(list1, 0, len(list1)-1, bar_width)
    elif sort_type == "Quick Sort":
        x = quicksort(list1, 0, len(list1)-1,bar_width)
    while True:
        if x == False:
            break
        # If the program is done and it didn't end by the back button the last sorted version of the list will be displayed 
        # untill the user either quits the program or presses back
        x = show(list1,bar_width)
        if x == False:
            break 
