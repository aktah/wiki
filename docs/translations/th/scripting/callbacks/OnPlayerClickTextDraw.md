---
id: OnPlayerClickTextDraw
title: OnPlayerClickTextDraw
description: Callback นี้ถูกเรียกเมื่อผู้เล่นคลิกบน Textdraw หรือยกเลิกโหมดการเลือกด้วยปุ่ม Escape
tags: ["player", "textdraw"]
---

:::warning

Callback นี้ถูกเพิ่มใน SA-MP 0.3e และจะไม่ทำงานในเวอร์ชั่นก่อนหน้านี้!

:::

## คำอธิบาย

Callback นี้ถูกเรียกเมื่อผู้เล่นคลิกบน Textdraw หรือยกเลิกโหมดการเลือกด้วยปุ่ม Escape

| ชื่อ      | คำอธิบาย                                                                         |
| --------- | ----------------------------------------------------------------------------- |
| playerid  | ไอดีของผู้เล่นที่เลือก Textdraw                                                      |
| clickedid | ไอดีของ Textdraw ที่ผู้เล่นคลิก หากการเลือกถูกยกเลิกจะเป็นค่า INVALID_TEXT_DRAW           |

## ส่งคืน

มันถูกเรียกในฟิลเตอร์สคริปต์ก่อนเสมอ ดังนั้นการส่งค่าคืนเป็น 1 จะบล็อกไม่ให้ฟิลเตอร์สคริปต์อื่น ๆ ได้เห็น

## ตัวอย่าง

```c
new Text:gTextDraw;

public OnGameModeInit()
{
    gTextDraw = TextDrawCreate(10.000000, 141.000000, "MyTextDraw");
    TextDrawTextSize(gTextDraw,60.000000, 20.000000);
    TextDrawAlignment(gTextDraw,0);
    TextDrawBackgroundColor(gTextDraw,0x000000ff);
    TextDrawFont(gTextDraw,1);
    TextDrawLetterSize(gTextDraw,0.250000, 1.000000);
    TextDrawColor(gTextDraw,0xffffffff);
    TextDrawSetProportional(gTextDraw,1);
    TextDrawSetShadow(gTextDraw,1);
    TextDrawSetSelectable(gTextDraw, 1);
    return 1;
}

public OnPlayerKeyStateChange(playerid, newkeys, oldkeys)
{
    if(newkeys == KEY_SUBMISSION)
    {
        TextDrawShowForPlayer(playerid, gTextDraw);
        SelectTextDraw(playerid, 0xFF4040AA);
    }
    return 1;
}

public OnPlayerClickTextDraw(playerid, Text:clickedid)
{
    if(clickedid == gTextDraw)
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

พื้นที่ที่สามารถคลิกได้ถูกกำหนดโดย TextDrawTextSize พารามิเตอร์ X และ Y ที่ส่งไปในฟังก์ชั่นต้องไม่ใช่ 0 หรือค่าติดลบ ห้ามใช้ CancelSelectTextDraw โดยไม่มีเงื่อนไขใน Callback นี้ อาจทำให้เกิดลูปไม่รู้จบ

:::

## ฟังก์ชั่นที่เกี่ยวข้องกัน

- [OnPlayerClickPlayerTextDraw](../../scripting/callbacks/OnPlayerClickPlayerTextDraw.md): ถูกเรียกเมื่อผู้เล่นคลิกบน Player-Textdraw
- [OnPlayerClickPlayer](../../scripting/callbacks/OnPlayerClickPlayer.md): ถูกเรียกเมื่อผู้เล่นคลิกคนอื่น
