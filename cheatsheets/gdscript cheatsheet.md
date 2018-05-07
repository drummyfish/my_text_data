work in progress

# GDScript

## Comparison with Python

Only the differences between the languages are mentioned.

| feature/construct  | Python | GDScript |
| ------------------ | ------ | -------- |
| garbage collection     | yes    | no (only reference counting) |
| 1st class citizen functions | yes | no (possible: `o.call("func_name",[])`)
| exceptions | `try` and `except` keywords | no
| built-in types           | basic:<br>`bool`, `int`, `float`, `complex`, `str`<br>container:<br>`list`, `dict`, `tuple`, `set`, ...     | basic:<br>`null`, `bool`, `int`, `float`, `String`<br>container:<br>`Array`, `Dictionary`, `PoolByteArray`, ... <br>vector:<br>`Vector2`, `Vector3`, `Rect2`, `Transform2D`,`Transform`, `Basis`, `Quat`, `AABB`<br>engine:<br>`Color`, `NodePath`, `RID`, `Object`
| basic constants        | `None`, `True`, `False` | `null`, `true`, `false` |
| constructor name | `__init__` | `_init`
| `self` variable | only in class functions, has to be an explicit argument (e.g. `__init__(self)`) | is always implicitly present (in non-static functions)
| variable definition    | `x = 5`                          | `var x = 5` <br> or to assign when the node is ready: <br> `onready var x = 5` <br> or to export to GUI interface and save: <br> `export var x = 5`
| call superclass method | `super(SelfClass,self).method()` | `.method()` |
| enumerations | `enum.Enum` class | `enum MyEnum {C1, C2, C3}` (syntactic sugar for constants)
| π            | `math.pi`                      | `PI`       |
| τ = 2π       | no                        | `TAU`      |
| ∞            | `math.inf` or `float("inf")`   | `INF`      |
| not a number | `float("nan")`, `math.isnan(x)` | `NAN`      |
| `is` keyword | test for identity | test for (sub)class |
| setters/getters | `@property` and `@x.setter` decorators | `var x = 5 setget x_setter, x_getter`
| switch/case  | no                             | `match expression:` <br> ` ` ` ` ` ` ` ` `patterns:` <br> ` ` ` ` ` ` ` ` ` ` ` ` ` ` ` ` `code # no break!`<br> ` ` ` ` ` ` ` ` `...` <br> ` ` ` ` ` ` ` ` `_:` <br> ` ` ` ` ` ` ` ` ` ` ` ` ` ` ` ` `default code # no break!` |
signals | no | declare: `signal sig(a,b)`<br>conn.:`o.connect("sig",o2,"cb",[1,2])`<br>emit:`emit_signal("sig",3,4)`
| coroutines | no | `yield` and `resume` keywords


## Script template

    # here there can possibly be the "tool" keyword
    
    # The script is a class, so it has to inherits from something:
    extends ClassName     # ClassName = class or subclass of the node the script is attached to
    
    # class variables go here, e.g.:
    # var memberVar = 5
    # const MEMBER_CONST = 10

    func _init():
        # constructor, called when the object is initialised 
        pass
        
    func _ready():
        # called when the node is added to scene
        pass
        
    #func _process(delta):
    #    # called each frame
    #    pass
