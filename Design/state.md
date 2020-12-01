# Managing State

Frontend state shared between components should be flattened and normalized as far as possible, just like you would with a database. Use getters (queries) to retrieve the state you want in the structure you need it in.

When managing form state, always treat it as strings (unless it is an array), and transform it to the necessary type at the edge of the system (e.g. in the API client). This is advisable because strings are the browser's native data type for form inputs. It's much easier to test transformations in specific functions at the edge of a system than at the bottom of a component tree.
