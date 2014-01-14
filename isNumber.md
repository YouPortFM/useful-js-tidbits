## To check to see if a variable is not a number:

This works regardless of whether the variable contains is a string or number.

    isNaN(num)     // returns true if the variable does NOT contain a valid number

### Examples:

    isNaN(123)     // false
    isNaN('123')   // false
    isNaN('foo')   // true
    isNaN('10px')  // true

Of course, you can negate this if you need to. For example, to implement the `IsNumeric` example you gave:

    function isNumeric(num){
        return !isNaN(num)
    }

## To convert a string containing a number into a number:

only works if the string *only* contains numeric characters, else it returns `NaN`.

    +num              // returns the numeric value of the string, or NaN if the 
                      // string isn't purely numeric characters
    
### Examples:

    +'12'             // 12
    +'foo'            // NaN
    +'12px'           // NaN

## To convert a string loosely to a number

useful for converting '12px' to 12, for example.

    parseInt(num)     // extracts a numeric value from the 
                      // start of the string, or NaN.

### Examples:

    parseInt('12')    // 12
    parseInt('aaa')   // NaN
    parseInt('12px')  // 12
    parseInt('foo2')  // NaN      These last two may be different
    parseInt('12a5')  // 12       from what you expected to see. 

## Floats

Bear in mind that, unlike `+num`, `parseInt` (as the name suggests) will convert a float into an integer by chopping off everything following the decimal point (if you want to use `parseInt()` *because of* this behaviour, you're probably better off with `Math.floor()` instead):

    parseInt(12.345)   // 12
    parseInt('12.345') // 12
    +'12.345'          // 12.345

## Empty strings

Empty strings may be a little counter-intuitive. `+num` converts empty strings to zero, and `isNaN()` assumes the same:

    +''                // 0
    isNaN('')          // false

But `parseInt()` does not agree:

    parseInt('')       // NaN
