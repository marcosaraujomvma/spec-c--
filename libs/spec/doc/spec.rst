.. Copyright 2007 (C) Dean Michael Berris <dean@orangeandbronze.com>
.. Distributed under the Boost Software License, Version 1.0.
.. (See accompanying file LICENSE_1_0.txt or copy at
.. http://boost.org/LICENSE_1_0.txt)

=====================================
Behavior Driven Development Interface
=====================================
--------------------
The Spec C++ Library
--------------------

The Spec C++ Library implements a Behavior Driven Development [0]_ (BDD)
Interface for specifying behavior of a program. The interface allows an 
alternative to the traditional Unit Testing interface of assertions to 
test the behavior of modules/units/components.

Below is shown the example of how the Spec library can be used in your test
suites:

::

    #include <boost/spec.hpp>
    #include <iostream>

    int main(int argc, char * argv[]) {
        using namespace boost::spec ;
        using namespace std;

        int an_int = 0;
        cout << "Please enter an integer: " << endl;
        cin >> an_int;
        try {
            value(an_int).should.be_greater_than(0);
            value(an_int).should.be_less_than(99);
            value(an_int).should.be_between(0).and_(99);
            value(an_int).should.equal(50);
        } catch (std::exception & e) {
            cerr << "Caught: " << e.what() << '\n';
        };
        return 0;
    };

Depending on what the user enters, the exception that is thrown by the
specifications will be displayed. Should the user enter ``50`` there will
be no exception thrown.

The library is developed to be part of the `Boost C++ Library`_.

----------
References
----------

.. _`Boost C++ Library`: http://boost.org/

.. [0] Behavior Driven Development: http://behaviour-driven.org/

---------------

| Copyright (C) 2007 Dean Michael Berris <dean@orangeandbronze.com> 
| Distributed under the Boost Software License, Version 1.0. (See accompanying file `LICENSE_1_0.txt` or copy at http://boost.org/LICENSE_1_0.txt)
