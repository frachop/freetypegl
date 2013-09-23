# defined in environment variables
CC:=clang
AR:=ar -r 
PROJECT_LOC:=..
WORKSPACE_LOC:=$(PROJECT_LOC)/..

TARGET_NAME:= freetype-gl
CONFIG_NAME:=release
CFLAGS:=$(SFLAGS) -O3 -DNDEBUG

#------------------------------------------------------------------------

TARGET_NAME:= lib$(TARGET_NAME).a
TARGET_DIR:= $(PROJECT_LOC)/lib
TARGET:= $(TARGET_DIR)/$(TARGET_NAME)

#------------------------------------------------------------------------

SRC_DIR:= $(PROJECT_LOC)/src
OBJ_DIR:= $(PROJECT_LOC)/.tmp/$(CONFIG_NAME)

SRC:= $(wildcard $(SRC_DIR)/*.c)
OBJS:= $(subst $(SRC_DIR)/, $(OBJ_DIR)/, $(SRC:.c=.o)) 
HEADERS:=  $(wildcard $(SRC_DIR)/*.hxx) $(wildcard $(SRC_DIR)/*.h) $(wildcard $(PROJECT_LOC)/include/freetypeGL/*.h)

#------------------------------------------------------------------------

INCLUDES:= -I$(WORKSPACE_LOC)/deps/include -I$(PROJECT_LOC)/include/freetypeGL
LIBS:=$(WORKSPACE_LOC)/deps/lib

CFLAGS:= $(CFLAGS) -W -Wall $(INCLUDES)

#------------------------------------------------------------------------

all: $(TARGET)

distclean: clean
	rm -rf $(TARGET_DIR)

clean:
	rm -rf $(OBJ_DIR)

$(TARGET): $(OBJS) 
	@mkdir -p $(TARGET_DIR)
	$(AR) $(TARGET) $(OBJS)

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c $(HEADERS) Makefile
	@mkdir -p $(OBJ_DIR)
	$(CC) $(CFLAGS) -o $@ -c $< 
	

	