Fix Fan Speed

Ganti RFAN atau GFAN Method return paling akhir "Return (Local0)" jadi "Return (FANS)" untuk hasil sensore yang lebih baik.
Method FAN0 bisa kalian ganti dengan re
Method (FAN0, 0, NotSerialized)
{
    Store (\_SB.PCI0.LPCB.EC0.TACH (Zero), Local0)
    Return (Local0)
}

Atau dengan (Yang ini jadi puluhan RPMnya)
Method (FAN0, 0, NotSerialized)
{
    Store (\_TZ.RFAN (Zero), Local0)
    Return (Local0)
}
