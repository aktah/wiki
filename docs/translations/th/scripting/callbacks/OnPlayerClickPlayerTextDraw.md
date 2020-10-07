---
id: OnPlayerClickPlayerTextDraw
title: OnPlayerClickPlayerTextDraw
description: Callback นี้ถูกเรียกเมื่อผู้เล่นคลิกที่ Player-Textdraw
tags: ["player", "textdraw", "playertextdraw"]
---

:::warning

Callback นี้ถูกเพิ่มใน SA-MP 0.3e และจะไม่ทำงานในเวอร์ชั่นก่อนหน้านี้!

:::

## คำอธิบาย

Callback นี้ถูกเรียกเมื่อผู้เล่นคลิกที่ Player-Textdraw มันจะไม่ถูกเรียกถ้าผู้เล่นยกเลิกโหมดการเลือก (ESC) - แต่ OnPlayerClickTextDraw ถูกเรียก

| ชื่อ           | คำอธิบาย                                             |
| ------------ | ------------------------------------------------------- |
| playerid     | ไอดีของผู้เล่นที่เลือก Textdraw                                |
| playertextid | ไอดีของ Player-Textdraw ที่ผู้เล่นเลือก                        |

## ส่งคืน

มันถูกเรียกในฟิลเตอร์สคริปต์ก่อนเสมอ ดังนั้นการส่งค่าคืนเป็น 1 จะบล็อกไม่ให้ฟิลเตอร์สคริปต์อื่น ๆ ได้เห็น

## ตัวอย่าง

```c
new PlayerText:gPlayerTextDraw[MAX_PLAYERS];

public OnPlayerConnect(playerid)
{
    // สร้าง Textdraw
    gPlayerTextDraw[playerid] = CreatePlayerTextDraw(playerid, 10.000000, 141.000000, "MyTextDraw");
    PlayerTextDrawTextSize(playerid, gPlayerTextDraw[playerid], 60.000000, 20.000000);
    PlayerTextDrawAlignment(playerid, gPlayerTextDraw[playerid],0);
    PlayerTextDrawBackgroundColor(playerid, gPlayerTextDraw[playerid],0x000000ff);
    PlayerTextDrawFont(playerid, gPlayerTextDraw[playerid], 1);
    PlayerTextDrawLetterSize(playerid, gPlayerTextDraw[playerid], 0.250000, 1.000000);
    PlayerTextDrawColor(playerid, gPlayerTextDraw[playerid], 0xffffffff);
    PlayerTextDrawSetProportional(playerid, gPlayerTextDraw[playerid], 1);
    PlayerTextDrawSetShadow(playerid, gPlayerTextDraw[playerid], 1);

    // ทำให้มันเลือกได้
    PlayerTextDrawSetSelectable(playerid, gPlayerTextDraw[playerid], 1);

    // แสดงมันให้กับผู้เล่น
    PlayerTextDrawShow(playerid, gPlayerTextDraw[playerid]);
    return 1;
}

public OnPlayerKeyStateChange(playerid, newkeys, oldkeys)
{
    if(newkeys == KEY_SUBMISSION)
    {
        SelectTextDraw(playerid, 0xFF4040AA);
    }
    return 1;
}

public OnPlayerClickPlayerTextDraw(playerid, PlayerText:playertextid)
{
    if(playertextid == gPlayerTextDraw[playerid])
    {
         SendClientMessage(playerid, 0xFFFFFFAA, "คุณคลิกบน Textdraw");
         CancelSelectTextDraw(playerid);
         return 1;
    }
    return 0;
}
```

## บันทึก

:::warning

เมื่อผู้เล่นกด ESC เพื่อยกเลิกการเลือก Textdraw ฟังก์ชั่น Callback OnPlayerClickTextDraw จะถูกเรียกและไอดี Textdraw จะเป็น 'INVALID_TEXT_DRAW' แต่กับ OnPlayerClickPlayerTextDraw จะไม่ถูกเรียกด้วย

:::

## ฟังก์ชั่นที่เกี่ยวข้องกัน

- [PlayerTextDrawSetSelectable](../../scripting/functions/PlayerTextDrawSetSelectable.md): ตั้งค่าให้ Player-Textdraw สามารถถูกเรียกผ่าน SelectTextDraw ได้หรือไม่
- [OnPlayerClickTextDraw](../../scripting/callbacks/OnPlayerClickTextDraw.md): ถูกเรียกเมื่อผู้เล่นคลิกบน Textdraw
- [OnPlayerClickPlayer](../../scripting/callbacks/OnPlayerClickPlayer.md): ถูกเรียกเมื่อผู้เล่นคลิกคนอื่น
