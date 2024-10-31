Here's a list of services and subservices provided by `INT 10h` for text mode in Intel 8088 assembly. For each service, I'll mention the values to place in `AX` and `BX` (if required). This list focuses on common text-related functionalities.

### INT 10h Services for Text Mode

1. **Set Video Mode**
   - **AX = 00h**
   - AL = Mode (e.g., 03h for 80x25 text mode)

2. **Set Cursor Type**
   - **AX = 0100h**
   - CH = Cursor Start Line (0-31, top 5 bits of cursor start)
   - CL = Cursor End Line (0-31, bottom 5 bits of cursor start)

3. **Set Cursor Position**
   - **AX = 0200h**
   - BH = Page number (0 for most basic usage)
   - DH = Row (0-24 for 25 rows)
   - DL = Column (0-79 for 80 columns)

4. **Read Cursor Position**
   - **AX = 0300h**
   - BH = Page number
   - Returns:
     - DH = Row
     - DL = Column

5. **Read Character and Attribute at Cursor**
   - **AX = 0800h**
   - BH = Page number
   - Returns:
     - AL = ASCII Character
     - AH = Attribute

6. **Write Character at Cursor with Attribute**
   - **AX = 0900h**
   - AL = ASCII Character
   - BH = Page number
   - BL = Attribute
   - CX = Number of times to write the character

7. **Write Character Only at Cursor**
   - **AX = 0Ah**
   - AL = ASCII Character
   - BH = Page number
   - CX = Number of times to write the character

8. **Set Active Display Page**
   - **AX = 0500h**
   - AL = Page number

9. **Scroll Active Page Up**
   - **AX = 0600h**
   - AL = Number of lines to scroll (0 = clear entire screen)
   - BH = Attribute for blank lines
   - CH = Row of upper-left corner
   - CL = Column of upper-left corner
   - DH = Row of lower-right corner
   - DL = Column of lower-right corner

10. **Scroll Active Page Down**
    - **AX = 0700h**
    - AL = Number of lines to scroll (0 = clear entire screen)
    - BH = Attribute for blank lines
    - CH = Row of upper-left corner
    - CL = Column of upper-left corner
    - DH = Row of lower-right corner
    - DL = Column of lower-right corner

11. **Set Text Window**
    - **AX = 0F00h**
    - Returns:
      - AL = Current mode
      - AH = Number of columns
