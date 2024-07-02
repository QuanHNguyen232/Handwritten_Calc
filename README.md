# Handwritten_Calc
Basic calculator, simulating 

Ideas + plan:
* Draw/Write: use react-canvas-draw API ([link](https://www.npmjs.com/package/react-canvas-draw)). This has all important functions such as undo, erase, etc. Our task now is to find how to save canvas as image, then send request to YOLO model
* Compute: using math.js API ([link](https://api.mathjs.org/)) (use POST). Header must contain `content-type: application/json`:
    * Example of POST request:
        ```json
        {
            "expr": [
            "a = 1.2 * 2 + 9/2",
            "a / 2",
            "5.08 cm in inch",
            "sin(45 deg) ^ 2",
            "9 / 3 + 2i",
            "b = [-1, 2; 3, 1]",
            "det(b)",
            "f(x, y) = x ^ y",
            "f(2, 3)",
            "y = 3",
            "x = 1-y",
            "f(x) = (sin(x) + cos(x/2)) * 5",
            "f(2)"
            ],
            "precision": 14
        }
        ```
    * Example of response:
        ```json
        {
            "result": [
                "6.9",
                "3.45",
                "2 inch",
                "0.5",
                "3 + 2i",
                "[[-1, 2], [3, 1]]",
                "-7",
                "f(x, y)",
                "8",
                "3",
                "-2",
                "f(x)",
                "7.2479986634691"
            ],
            "error": null
        }
        ```
* Write output on canvas:
    * how to show output on canvas?
    * position: row: average of the equation; col: after `=` sign.