Fix Fan Speed

Ganti RFAN atau GFAN Method return paling akhir "Return (Local0)" jadi "Return (FANS)" untuk hasil sensore yang lebih baik.
Method (RFAN, 1, NotSerialized)
{
    If (\_SB.PCI0.SBRG.EC0.ECAV ())
    {
        Store (\_SB.PCI0.SBRG.EC0.ST83 (Arg0), Local0)
        If (LEqual (Local0, 0xFF))
        {
            Return (Local0)
        }
        Store (\_SB.PCI0.SBRG.EC0.TACH (Arg0), Local0)
        Divide (Local0, 0x64, Local1, Local0)
        Add (Local0, One, Local0)
        If (LLessEqual (Local0, 0x3C))
        {
            Store (Local0, FANS)
        }
        Else
        {
            Store (FANS, Local0)
        }
    }
    Else
    {
        Store (Zero, Local0)
    }
    Return (Local0) // Ganti dengan Return (FANS)
}



Method FAN0 bisa kalian ganti dengan re
Method (FAN0, 0, NotSerialized)
{
    Store (\_SB.PCI0.SBRG.EC0.TACH (Zero), Local0)
    Return (Local0)
}



Atau dengan (Yang ini jadi puluhan RPMnya)
Method (FAN0, 0, NotSerialized)
{
    Store (\_TZ.RFAN (Zero), Local0)
    Return (Local0)
}
