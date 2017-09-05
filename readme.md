# Style
Rather than define another coding standard I think more value can be gained
from separating good practices applicable to programming in general and largely
subjective aesthetics qualities (like brace usage).

# Minimise mutable state
A philosophy I hadn't considered until I started looking at functional
programming. Minimise mutable state (use constants) and minimise unexpected
side effects.

```js
// JavaScript
const hello = 5
```

```haskell
-- Everything is immutable in Haskell :O
hello = 5
```

```cpp
// C++
// Ignoring the fact that you can cast away constness :(
const int hello = 5;
```

```bash
# bash
readonly hello=5
```

# Scope
Scope as tightly as possible.

```cpp
// No thanks
// using namespace std;

void print() {

  // Yes please
  using namespace std;
  cout << "hello" << endl;
}
```

```bash
function hello() {

  local message="hi"
  echo $message
}
```

# Simple syntax
Use features of the language to simplify the code (see "Scope" above).

```cpp
// C++ - local namespace declaration to simplify scope
if (debug)
  std::cout << "debug" << std::endl;

using namespace std;

if (debug)
  cout << "debug" << endl;
  ```

# Brace usage
It's fairly arbitrary where you put your braces: see
[Wikipedia](https://en.wikipedia.org/wiki/Indent_style).

At work I use Allman style.

```cpp
// C++
if (true)
{
  // This and that
  ++a;
}
```

When it's up to me I prefer K&R-style. Usually with a newline after the opening
brace to make it look more balanced.

```js
// JavaScript
if (true) {

  // This and that
  ++a
}
```

```bash
# bash
if true; then

  # This and that
  (( ++a ))
fi
```

# Semicolons in JavaScript
I started dropping semicolons in JavaScript but both Greasemonkey editors
(Firefox and Chrome) complain a lot about this so I've returned to using them
again.

```js
// Periodically check reload checkbox state
setInterval(function() {
            if (window.location.href.split("?").pop() === "reload")
            window.location.reload()
            }, 2000)
```

# clang-format
In C++ you can simply run ```clang-format``` over your code and these
distractions go away. I haven't quite worked out where it fits into my workflow
but in the meantime I've just added it as a separate make rule.

# Limited by your imagination
It's usually used as a motivational mantra but actually we are entirely limited
by our imagination. Eureka moments are often completely accidental but by
putting yourself in the right environment/mindset I think you can improve you
chances of coming across one.

# Use software as the end user
How can you include the things you write into your daily routine? It's really
difficult. Perhaps you could just use a small part of something? Overlay the
results of the API read you're working on into your commute website with
Greasemonkey?

# Hungarian notation
Decorating a variable/class/constant with letters to indicate its underlying
type: it is a little harder to maintain but mostly I think it looks clumsy.

https://en.wikipedia.org/wiki/Hungarian_notation

# Interruptions
Interruptions can really mess with your flow. It's easy to interrupt the person
next to you but it's no good for them. I'm conscious of not stopping somebody
when they're deep in the middle of something, waiting until somebody else
interrupts them (...) or just sending an email instead.

# Pseudo code
The use of ad-hoc, informal code is common in high-level documents but is prone
to ambiguities. Why not use actual code?

# Embracing Wagile
There are a whole generation of system engineers and managers who aren't letting
waterfall go any time soon. So how can we embrace wagile?

Often managers interpret Agile as impulsive or responsive but the important
thing for me is dropping the things that seemed like a good idea but don't work
in practice.

We should be open to new solutions all the time.

http://ronjeffries.com/articles/016-03/you-want/

# Code editors
I use vim for configuring embedded systems (sometimes the only way) and small
code projects but for larger code bases where there are a lot of files to keep
in your head it's better to use an IDE.

# Compiler optimisation
I normally prefer to defer enabling compiler optimisation until the code is
mature. Only then should you enable the speed ups. (In my day job we prefer to
only enable compiler optimisation because it's cheaper.) Is it acceptable if
your code is only quick enough when the optimiser is cranked?

# Compiler warnings
Turn warnings up and read them. I prefer the warnings offered by ```clang``` but it's useful to swap to
```gcc``` and see what it has to offer.

```bash
# g++
-Wall -Wpedantic -pedantic-errors

# clang++
-Weverything
```

# 2D graphics
Initially I was unsure about adding 2D graphics to the language but I've come
around to it.

# Touch typing
Often not taken seriously but if you type all day why wouldn't you want to do
it quicker? Of course typing code doesn't flow quite as well as sentences but
you still have to communicate your ideas.

# Commit often
And make the merge smoother.

# Calibration
There's a curious use of the word calibration in my work. For me it means an
improved performance from a default state. But on all systems I've worked on it
has this definition:

1. Calibrated: has a fighting chance of behaving as expected.
2. Uncalibrated: does nothing.

# Prefer long and long long
http://en.cppreference.com/w/cpp/language/types

# Further reading
* https://blog.codinghorror.com/code-smells/
