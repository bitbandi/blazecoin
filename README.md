Blazecoin Core integration/staging tree
=======================================

http://blazeco.in

What is Blazecoin?
------------------

Blazecoin is a fork of Litecoin version with fast block time and faster
confirmations (2 confirmations needed instead of 6).
Like Litecoin it uses scrypt as a proof of work scheme.

License
-------

Blazecoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see http://opensource.org/licenses/MIT.

Specifications
--------------

    - 30 second block target
    - Difficulty retargets every 1 hour  (which means every 120 blocks it retargets)
    - Total coins will be around 2,065,000,000.
    - Block rewards will be 413 coins per block
    - Block subsidy halves once per year.
    - The default ports are 55414 (connect) and 55413 (json rpc).
    - First 100 blocks only receive 13 coins
    - Premined 1% in order to do matching fire grants. (Read more in the foundation area)

Development tips and tricks
---------------------------

**compiling for debugging**

Run configure with the --enable-debug option, then make. Or run configure with
CXXFLAGS="-g -ggdb -O0" or whatever debug flags you need.

**debug.log**

If the code is behaving strangely, take a look in the debug.log file in the data directory;
error and debugging messages are written there.

The -debug=... command-line option controls debugging; running with just -debug will turn
on all categories (and give you a very large debug.log file).

The Qt code routes qDebug() output to debug.log under category "qt": run with -debug=qt
to see it.

**testnet and regtest modes**

Run with the -testnet option to run with "play blazecoins" on the test network, if you
are testing multi-machine code that needs to operate across the internet.

If you are testing something that can run on one machine, run with the -regtest option.
In regression test mode, blocks can be created on-demand; see qa/rpc-tests/ for tests
that run in -regtest mode.

**DEBUG_LOCKORDER**

Blazecoin Core is a multithreaded application, and deadlocks or other multithreading bugs
can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure
CXXFLAGS="-DDEBUG_LOCKORDER -g") inserts run-time checks to keep track of which locks
are held, and adds warnings to the debug.log file if inconsistencies are detected.
