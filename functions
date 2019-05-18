
#
# UTILITY FUNCTIONS FOR REMOVING COMMENTS FROM CODE
#


def remove_only_octothorpes(code):
    return code.replace('#', '')
    """
    Removes the octothorpes from the text in the parameter code.
    :param code: Text. Possibly valid Python code.
    :return: The same text but with all the octothorpes removed. Code that was valid before may be invalid after this.
    """
'''
For example, if this is the text in the parameter code (between and excluding the hyphens):
-----------------------------
def hello_world():        # this is a comment
    print("Hello world!") # this is another comment
print("I # like # octothorpes # .")
-----------------------------
then the string that you return should look like this (between and excluding the hyphens):
-----------------------------
def hello_world():         this is a comment
    print("Hello world!")  this is another comment
print("I  like  octothorpes  .")
-----------------------------
(Highlight the text to see exactly where the spaces are.)
'''


def remove_octothorpe_and_after(code):
    """
    Checks every line of the code and chops off everything at 
    and after the octothorpe on each line (if there is one).
    If the line has no octothorpe then it is left unchanged. 
    Returns the code with this change applied.
    :param code: Text. Possibly valid Python code.
    :return: The same text but with each line chopped at the octothorpe. Code that was valid before may be invalid after this.
    """
    
    
    lines = code.split('\n');
    buf = ''
    for l in lines:
        i = l.find('#')
        if i >= 0:
            buf = buf + l[0:i]
        else:
            buf = buf + l
        if l != lines[-1]:
            buf = buf + '\n'
    return buf
'''
For example, if this is the text in the parameter code (between and excluding the hyphens):
-----------------------------
def hello_world():        # this is a comment
    print("Hello world!") # this is another comment
print("I # like # octothorpes # .")
-----------------------------
then the string that you return should look like this (between and excluding the hyphens):
-----------------------------
def hello_world():        
    print("Hello world!") 
print("I 
-----------------------------
(Highlight the text to see exactly where the spaces are.)
'''


def remove_single_line_comments(code):
    """
    Checks every line of the code and removes single line comments. 
    Does not remove octothorpes that are inside string literals. 
    Returns the code with this change applied.
    :param code: Valid Python code. This code may contain strings which have octothorpes in them. These strings are not comments.
    :return: The same text but with single line comments removed. Code should be valid and logically equivalent to the original code.
    Hints: - In order to do this you need to think about what defines a string literal.
           - Consider the code/text from the computer's point of view, not your own.
    """

    lines = code.split('\n');
    buf = ''
    for l in lines:
        if l.find('#') >= 0:
            commentStart = -1
            stack = []
            for i in range(0, len(l)):
                c = l[i]
                if c == '\"' or c == '\'':
                    if i == 0 or l[i-1] != '\\':
                        if len(stack) > 0:
                            if stack[-1] == c:
                                stack.pop()
                        else:
                            stack.append(c)
                elif c == '#' and len(stack) == 0:
                    commentStart = i
                    break
            if commentStart >= 0:
                buf = buf + l[:commentStart]
            else:
                buf = buf + l
        else:
            buf = buf + l
        if l != lines[-1]:
            buf = buf + '\n'
    return buf
'''
For example, if this is the text in the parameter code (between and excluding the hyphens):
-----------------------------
def hello_world():        # this is a comment
    print("Hello world!") # this is another comment
"""# this is a comment
This is a multiline comment
with a single line comment # this is a comment
inside of it.
"""
print("I # like # octothorpes # .")
-----------------------------
then the string that you return should look like this (between and excluding the hyphens):
-----------------------------
def hello_world():        
    print("Hello world!") 
"""
This is a multiline comment
with a single line comment 
inside of it.
"""
print("I # like # octothorpes # .")
-----------------------------
(Highlight the text to see exactly where the spaces are.)
'''



#
# STAND-ALONE FUNCTIONS RELATING TO GAMES
#
# Note: Do not assume that maps are perfectly rectangular. Rows can be of different lengths.
#

def get_square(map, x, y, out_of_bounds_char):
    """
    Returns the square in the map at the (x, y) location if the location
    is within bounds, or the out_of_bounds_char if (x, y) is outside of bounds.
    :param map: The two-dimensional array (i.e. list of lists) that we are examining.
    :param x: Horizontal position.
    :param y: Vertical position.
    :param out_of_bounds_char: The character to return if either x or y is out of bounds.
    :return: The character at the (x, y) position in the map.
    """
    
    if x < 0 or y < 0 or y >= len(map):
        return out_of_bounds_char
    
    row = map[y]
    if x >= len(row):
        return out_of_bounds_char
    return row[x]
#'''
#For example, if the map looks like this:
SOME_MAP = [[ 'a', 'b', 'c', 'd' ],
            [ 'e', 'f', 'g', 'h' ],
            [ 'i', 'j', 'k', 'l' ]]
#then the following function calls would return these values:
get_square(SOME_MAP, 0, 2, 'X')#  -->  'i'
get_square(SOME_MAP, 3, 0, 'X')#  -->  'd'
get_square(SOME_MAP, 4, 3, 'X')#  -->  'X'
get_square(SOME_MAP, 0, -1, 'X')#  -->  'X'
get_square(SOME_MAP, -3, 1, 'X')#  -->  'X' 
#'''


def set_square(map, x, y, new_value):
    """
    Sets the square in the map at the (x, y) location and returns True if the location is within bounds,
    or returns False if (x, y) is outside of bounds.
    :param map: The two-dimensional array (i.e. list of lists) that we are examining.
    :param x: Horizontal position.
    :param y: Vertical position.
    :param new_value: The new value to assign at (x, y).
    :return: True if (x, y) is within bounds and you could set the value or False if not.
    """
    
    if x < 0 or y < 0 or y >= len(map):
        return False
    
    row = map[y]
    if x >= len(row):
        return False
    row[x] = new_value
    return True
    
    
    pass
'''
Examples of calling set_square() and return values:
SOME_MAP = [[ 'a', 'b', 'c', 'd' ],
            [ 'e', 'f', 'g', 'h' ],
            [ 'i', 'j', 'k', 'l' ]]
set_square(SOME_MAP, 1, 0, 'W') --> True
and now SOME_MAP looks like this:
SOME_MAP = [[ 'a', 'W', 'c', 'd' ],
            [ 'e', 'f', 'g', 'h' ],
            [ 'i', 'j', 'k', 'l' ]]
Then, separately...
set_square(SOME_MAP, -1, 0, 'W') --> False
and SOME_MAP is not changed.
'''


def get_map_from_user():
    """
    Asks the user to type in a custom map. Saves each line of text that 
    the user enters as a separate row. An empty line ends the process.
    :return: The two-dimensional array (i.e. list of lists) of characters that the user has typed in.
    """
    result = []
    while True:
        inp = input("Enter row")
        if inp == "":
            return result
        
        row = []
        for c in inp:
            row.append(c)
        result.append(row)

    return result
'''
For example, if the user types this (between and excluding the lines of hyphens):
--------------
  hello
this is a 
map!   

--------------
(Highlight the text to see exactly where the spaces are.)
then the map should look like this:
[[' ', ' ', 'h', 'e', 'l', 'l', 'o'],
 [', 't', 'h', 'i', 's ', 'i', 's', ' ', 'a'], 
 ['m', 'a', 'p', '!', ' ', ' ', ' ']]
Notice that spaces are kept, rows can be different lengths, and the 
blank line that ends the process is not part of the result.
If the user just hits ENTER without typing anything, it would look
like this (between and excluding the lines of hyphens):
--------------

--------------
and the result would be an empty map with no rows:
[]
'''


def extract_positions(map, player, werewolf):
    """
    Looks through the map for a 'P' (capital P) character and 'W' (capital W)
    character that mark the positions of the Player and Werewolf and assigns 
    the corresponding column and row values to the x and y attributes of 
    player and werewolf, respectively.
    :param map: The two-dimensional array (i.e. list of lists) of characters that we are examining.
    :param player: Player info object.
    :param werewolf: Werewolf info object.
    """
    
    for i in range(len(map)):
        row = map[i]
        for j in range(len(row)):
            c = row[j]
            if c == 'P':
                player.x = j
                player.y = i
            elif c == 'W':
                werewolf.x = j
                werewolf.y = i
'''
For example, if the map looks like this:
[[ ' ', ' ', '.', 'P'],
 [ ' ', 'W', '.', '.']]
then after this code executes...
   player.x should be 3
   player.y should be 0
   werewolf.x should be 1
   werewolf.y should be 1
'''


def clear_screen():
    lines = ''
    while len(lines) != 99:
        lines = lines + '\n'
    print(lines)
    
    
    """
    Displays 100 blank lines to the screen. Must be completely blank, without any extra characters
    """
    pass


def print_map_or_section(map_or_section):
    """
    Display the map (or section of map) to the screen.
    :param map_or_section: The two-dimensional array (i.e. list of lists) that we are examining.
    """
    
    for i in range(len(map_or_section)):
        line = ''
        row = map_or_section[i]
        for j in range(len(row)):
            line = line + row[j]
        print(line)
'''
For example, if the map_or_section looks like this:
[[' ', ' ', 'h', 'e', 'l', 'l', 'o'],
 [', 't', 'h', 'i', 's ', 'i', 's', ' ', 'a'], 
 ['m', 'a', 'p', '!', ' ', ' ', ' ']]
then you should display this (between and excluding the lines of hyphens):
--------------
  hello
this is a 
map!   
--------------
(Highlight the text to see exactly where the spaces are.)
'''


def make_map_section(map, x, y, width, height, out_of_bounds_char):
    """
    Returns a copy of a section of the map starting from (x, y). Any integer values for x and y are valid.
    :param map: The two-dimensional array (i.e. list of lists) of characters that we are examining.
    :param x: The horizontal position. Any integer value is valid.
    :param y: The vertical position. Any integer value is valid.
    :param width: How many characters wide this section is.
    :param height: How many characters tall this section is.
    :param out_of_bounds_char: The character to use for points outside of the natural bounds of the map.
    :return: A two-dimensional array of characters containing the specified section of the map.
    """
    result = []
    for i in range(y, y + height):
        line = []
        if i >= 0 and i < len(map):
            row = map[i]
            for j in range(x, x + width):
                if j >= 0 and j < len(row):
                    line.append(row[j])
                else:
                    line.append(out_of_bounds_char)
        else:
            for j in range(x, x + width):
                line.append(out_of_bounds_char)
        result.append(line)
                    
    return result
    
'''
#For example, if the map looks like this:
SOME_MAP = [[ 'a', 'b', 'c', 'd' ],
            [ 'e', 'f', 'g', 'h' ],
            [ 'i', 'j', 'k', 'l' ],
            [ 'm', 'n', 'o', 'p' ]]
then the following function calls would return the corresponding results:
make_map_section(SOME_MAP, 1, 0, 3, 2, '#') --> [[ 'b', 'c', 'd' ], [ 'f', 'g', 'h' ]]
make_map_section(SOME_MAP, -1, -1, 2, 3, '#') --> [[ '#', '#'], ['#', 'a'], ['#', 'b']]
make_map_section(SOME_MAP, 3, 3, 3, 3, '@') --> [[ 'k', 'l', '@' ], [ 'o', 'p', '@' ], [ '@', '@', '@' ]]
make_map_section(SOME_MAP, 1, 2, 0, 0, '$') --> []
make_map_section(SOME_MAP, -1, -2, 0, 0, '$') --> []
make_map_section(SOME_MAP, -1, -2, 1, 1, '$') --> [[ '$' ]]
'''


def print_map_section(map, x, y, width, height, out_of_bounds_char):
    """
    Displays a section of the map starting from (x, y). Any integer values for x and y are valid.
    :param map: The two-dimensional array (i.e. list of lists) of characters that we are examining.
    :param x: The horizontal position. Any integer value is valid.
    :param y: The vertical position. Any integer value is valid.
    :param width: How many characters wide this section is.
    :param height: How many characters tall this section is.
    :param out_of_bounds_char: The character to use for points outside of the natural bounds of the map.
    :return:
    """
    
    print_map_or_section(make_map_section(map, x, y, width, height, out_of_bounds_char))
