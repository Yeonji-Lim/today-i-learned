**

def get_length(value):

    length = 0

    while value > 0:

        value //= 10

        length += 1

    return length

**