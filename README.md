// NUMBER SYSTUM CONVERTOR

#include <iostream>
#include <cmath>
#include <string.h>
using namespace std;

void name_list(){
    cout << " (1)  decimal to binary\n";
    cout << " (2)  binary to decimal\n";

    cout << " (3)  decimal to octual\n";
    cout << " (4)  octual to decimal\n";

    cout << " (5)  decimal to hecsadecimal\n";
    cout << " (6)  hecsadecimal to decimal\n";

    cout << " (7)  binary to octual\n";
    cout << " (8)  octual to binary\n";

    cout << " (9)  binary to hecsadecimal\n";
    cout << " (10) hecsadecimal to binary\n";

    cout << " (11) octual to hecsadecimal\n";
    cout << " (12) hecsadecimal to octual\n";

    cout << "please enter conversion number you want\n";
}

void decimal_to_other(int b, float c, int r)
{
    int other[30];
    char hex_to_dec[30];
    int i = 0;
    //for integer part of the value.
    while (b > 0)
    {
        other[i] = (int)b % r;
        b = b / r;
        //only for decimal to hexadecimal.
        if (r == 16)
        {
            if (other[i] < 10)
            {
                hex_to_dec[i] = other[i] + 48;
            }
            else
            {
                hex_to_dec[i] = other[i] + 55;
            }
        }

        i++;
    }
    for (int j = i - 1; j >= 0; j--)
    {
        if (r == 16)
        {
            cout << hex_to_dec[j];
        }
        else
        {
            cout << other[j];
        }
    }
    cout << ".";
    for (int i = 0; i < 8; i++)
    {
        int l;
        char htd;
        c = c * r;
        l = c;
        if (r == 16)
        {
            if (l < 10)
            {
                htd = l + 48;
            }
            else
            {
                htd = l + 55;
            }
            cout << htd;
        }
        else
        {
            cout << l;
        }
        c = c - l;

        if (c == 0)
        {
            break;
        }
    }
}

double other_to_decimal(string sa, string sb, int r)
{
    // int len = sa.length();
    int base = 0;
    int dec_val = 0;
    for (int i = sa.length() - 1; i >= 0; i--)
    {
        if (sa[i] >= '0' && sa[i] <= '9')
        {
            dec_val += (sa[i] - 48) * pow(r, base);
        }
        else if (sa[i] >= 'A' && sa[i] <= 'F')
        {
            dec_val += (sa[i] - 55) * pow(r, base);
        }
        base++;
    }


    int base1 = -1;
    float dec_val1;
    for (int i = 0; i < sb.length(); i++)
    {
        if (sb[i] >= '0' && sb[i] <= '9')
        {
            dec_val1 += (sb[i] - 48) * pow(r, base1);
        }
        else if (sb[i] >= 'A' && sb[i] <= 'F')
        {
            dec_val1 += (sb[i] - 55) * pow(r, base1);
        }
        base--;
    }
    return dec_val + dec_val1;
}

int main()
{
    name_list();
    int num;
    cin >> num;
    cout<<"please enter nmber in farctional number form (number.0) from: "<<endl;
    string value;
    cin >> value;

    string sa = value.substr(0, value.find("."));
    string sb = value.substr(value.find(".") + 1, value.size());

    int b;
    float c;
    double output;

    if (num == 1 || num == 3 || num == 5)   //changing charactor intonumerical value
    {
        b = stoi(sa);
        c = stoi(sb);
        c = c / pow(10, sb.size());
    }

    if (num == 1) //decimal to binary
    {
        int r = 2;
        decimal_to_other(b, c, r);
    }

    if (num == 2) //binary to decimal
    {
        int r = 2;
        output = other_to_decimal(sa, sb, r);
        cout << output;
    }

    if (num == 3) //decimal to octual
    {
        int r = 8;
        decimal_to_other(b, c, r);
    }

    if (num == 4) //octual to decimal
    {
        int r = 8;
        output = other_to_decimal(sa, sb, r);
        cout << output;
    }

    if (num == 5) //decimal to hecsadecimal
    {
        int r = 16;
        decimal_to_other(b, c, r);
    }

    if (num == 6) //hecsadecimal to decimal
    {
        int r = 16;
        output = other_to_decimal(sa, sb, r);
        cout << output;
    }

    if (num == 7) //binary to octual
    {
        int r = 2;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 8;
        decimal_to_other(b, c, r);
    }

    if (num == 8) //octual to binary
    {
        int r = 8;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 2;
        decimal_to_other(b, c, r);
    }

    if (num == 9) //binary to hecsadecimal
    {
        int r = 2;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 16;
        decimal_to_other(b, c, r);
    }

    if (num == 10) //hecsadecimal to binary
    {
        int r = 16;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 2;
        decimal_to_other(b, c, r);
    }

    if (num == 11) //octual to hecsadecimal
    {
        int r = 8;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 16;
        decimal_to_other(b, c, r);
    }

    if (num == 12) //hecsadecimal to octual
    {
        int r = 16;
        output = other_to_decimal(sa, sb, r);
        b = (int)output;
        c = output - b;
        r = 8;
        decimal_to_other(b, c, r);
    }

    return 0;
}
