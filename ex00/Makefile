# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: ibertran <ibertran@student.42lyon.fr>      +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2024/07/13 00:18:40 by ibertran          #+#    #+#              #
#    Updated: 2024/07/20 01:23:15 by ibertran         ###   ########lyon.fr    #
#                                                                              #
# **************************************************************************** #

NAME = rush-02

# *** FILES ****************************************************************** #

MAKE_DIR := .make/
BUILD_DIR := $(MAKE_DIR)$(shell git branch --show-current)/

SRCS_DIR = srcs/
SRCS = $(addsuffix .c, $(SRC))

OBJS = $(patsubst %.c,$(BUILD_DIR)%.o,$(SRCS))

DEPS = $(patsubst %.o,%.d,$(OBJS))

SRC = \
	main


# *** LIBRARIES && INCLUDES  ************************************************* #

INCS_DIR = incs/
INCS = \
	$(INCS_DIR) \

# *** CONFIG ***************************************************************** #

CC			=	cc
CFLAGS		=	-Wall -Wextra -Werror

DEFINES		=

CPPFLAGS 	=	$(addprefix -I, $(INCS)) \
				$(addprefix -D, $(DEFINES)) \
				-MMD -MP \

MAKEFLAGS	=	--no-print-directory

-include $(DEPS)

# *** TARGETS **************************************************************** #

.PHONY : all
all : $(NAME)

$(NAME) : $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $(NAME)

$(BUILD_DIR)%.o : $(SRCS_DIR)%.c
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) $(CPPFLAGS) -c $< -o $@

.PHONY : clean
clean :
	rm -rf $(BUILD_DIR)

.PHONY : fclean
fclean :
	rm -rf $(MAKE_DIR) $(NAME)

.PHONY : re
re : fclean
	$(MAKE)
