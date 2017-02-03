 
Conclusions
===========

We have seen very quickly how to create a project to develop a gvSIG 2.2 functionality. This is not only a way developing for gvSIG, in fact we can note that this is quite ordinary way to develop, by separating the different layers of abstraction that can be found in the development:

- Business logic
- User interface
- Integration with gvSIG

And for each of them it is clearly marked which part is API and which is implementation.

Not only we are bring a new functionality to gvSIG, we offer a functionality that can be reused by other developments through a well-defined API, being able to benefit from other projects that have packaged their functionality as a library.

In addition we benefit from the Maven engine that allows us to deliver these libraries so that they are easily accessible to other developers.


