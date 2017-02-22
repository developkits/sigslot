## Hello world for sigslot(http://sigslot.sourceforge.net/)


```c++
#include <iostream>
#include "sigslot.h"

using namespace sigslot;

class Switch
{
public:
    signal0<> clicked;
};

class Light : public has_slots<>
{
public:
    void turn_on()
    {
        std::cout << "Turn on ~" << std::endl;
    }
};

int main(int argc, char *argv[])
{
    Light lit1;
    Switch swh;

    swh.clicked.connect(&lit1, &Light::turn_on);
    swh.clicked.emit();

    return 0;
}
```
