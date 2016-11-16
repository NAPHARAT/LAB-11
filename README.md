#ใบงานที่ 11
##การเขียนโปรแกรมกราฟฟิกส์ด้วย GDI+ (3)
##นางสาวนภารัตน์ ฐิติกรโกวิท 57030180
## กล่าวนำ
ใบงานนี้ มีวัตถุประสงค์ เพื่อให้นักศึกษา ได้รู้จักกับ GDI+ ซึ่งจะช่วยให้นักษาสามารถ

* วาดรูปร่างต่างๆ โดยใช้ GDI+ ได้

## การใช้งานแปรงระบายสี (Brush)
แปรงระบายสี ช่วยให้เราสามารถระบายสีแบบต่างๆ ให้กับรูปร่างต่างๆ ได้ตามต้องการ ใน GDI+ มีแปรงระบายสีอยู่ 5 รูปแบบด้วยกัน ประกอบด้วย ```SolidBrush```, ```HatchBrush```, ```TextureBrush```, ```LinearGradientBrush``` และ ```PathGradientBrush``` ซึ่งทั้งหมดจะอยู่ในคลาส ```Brush``` 

### การระบายสีด้วย SolidBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-1.png">
</p>


Code
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Point[] pt = {  new Point (10,22),
                            new Point (188,246),
                            new Point (280,192),
                            new Point (250,48)

            };
            e.Graphics.FillClosedCurve(Brushes.Blue, pt);
            e.Graphics.DrawClosedCurve(Pens.Red, pt);
        }
    }
}


```

ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/1.JPG)

### การระบายสีด้วย HatchBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
 <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-2.png">
</p>



Code
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {

            this.SetClientSizeCore(500, 600);
            HatchBrush brush;
            int x = 20;
            int y = 20;
            foreach (HatchStyle brushStyle in Enum.GetValues (typeof(HatchStyle )))
            {
                brush = new HatchBrush(brushStyle, Color.Navy, Color.Yellow);
                e.Graphics.FillRectangle(brush, x, y, 40, 20);
                y += 30;
                if((y+30)>this.ClientSize .Height )
                {
                    y = 20;
                    x += 180;
                }
            }
            
        }
    }
}

```


ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/2.JPG)
### การระบายสีด้วย TextureBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-3.png">
</p>
**หมายเหตุ** ชื่อรูปในบรรทัดที่ 22 ให้เปลี่ยนเป็นที่ตั้งจริงของรูปที่นักศึกษาใช้



Code
```

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            Image image = Image.FromFile("d:\\1.PNG");
            TextureBrush brush = new TextureBrush(image);
            Rectangle rect = new Rectangle(10, 10, 180, 150);
            e.Graphics.FillEllipse(brush, rect);
        }
        }
    }

```

ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/3.JPG)
### การระบายสีด้วย TextureBrush
* ให้วางคอนโทรล Panel จำนวน 2 ตัวลงบน Form โดยมีชื่อว่า panel1 และ panel2 ตามลำดับ
 * เพิ่ม paint event ให้กับ panel ทั้งสองตัว
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-4.png">
</p>
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen1_Paint(object sender, PaintEventArgs e)```
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-5.png">
</p> 




Code
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {



        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {
            LinearGradientBrush pnlGdt =
                new LinearGradientBrush(panel1.ClientRectangle, Color.Yellow, Color.Navy,0f, true);
            e.Graphics.FillRectangle(pnlGdt, panel1.ClientRectangle);
            pnlGdt.Dispose();
        }

      
    }
    }

```



ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/4.JPG)
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen2_Paint(object sender, PaintEventArgs e)```
   <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-6.png">
</p>

Code

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {



        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {
            LinearGradientBrush pnlGdt =
                new LinearGradientBrush(panel1.ClientRectangle, Color.Yellow, Color.Navy, 0f, true);
            e.Graphics.FillRectangle(pnlGdt, panel1.ClientRectangle);
            pnlGdt.Dispose();
        }

        private void panel2_Paint(object sender, PaintEventArgs e)
        {
            LinearGradientBrush pnlGdt =
                new LinearGradientBrush(panel2.ClientRectangle, Color.Yellow, Color.Navy, 90f, true);
            e.Graphics.FillRectangle(pnlGdt, panel2.ClientRectangle);
            pnlGdt.Dispose();

        }
      
    }
    }



```

ผลการทดลอง

![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/5.JPG)


### การระบายสีด้วย Path Gradient Brush

การระบายสีด้วย Path Gradient Brush เป็นการไล่เฉดสีตาม path ที่กำหนด ในโปรแกรมตัวอย่างนี้จะวาดวงรีและไล่เฉดสีจากด้านในออกสู่ด้านนอก
* การทดลอง 
 * ให้ลดขนาด panel1 และ panel2 ลง แล้วเพิ่ม panel3 เข้าไปใน form1 ดังรูป
    <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-7.png">
</p>

 * เพิ่ม Paint event ให้กับ Panel3
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen3_Paint(object sender, PaintEventArgs e)```
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-8.png">
</p>

Code
```

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace Lab11
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {



        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {
            LinearGradientBrush pnlGdt =
                new LinearGradientBrush(panel1.ClientRectangle, Color.Yellow, Color.Navy, 0f, true);
            e.Graphics.FillRectangle(pnlGdt, panel1.ClientRectangle);
            pnlGdt.Dispose();
        }

        private void panel2_Paint(object sender, PaintEventArgs e)
        {
            LinearGradientBrush pnlGdt =
                new LinearGradientBrush(panel2.ClientRectangle, Color.Yellow, Color.Navy, 90f, true);
            e.Graphics.FillRectangle(pnlGdt, panel2.ClientRectangle);
            pnlGdt.Dispose();

        }

        private void panel3_Paint(object sender, PaintEventArgs e)
        {
            GraphicsPath path = new GraphicsPath();
            path.AddEllipse(panel3.ClientRectangle);
            PathGradientBrush br = new PathGradientBrush(path);
            br.CenterPoint = new PointF(panel3.ClientRectangle.Width / 2, panel3.ClientRectangle.Height / 2);
            br.CenterColor = Color.Navy;
            br.SurroundColors = new Color[] { Color.Yellow };
            e.Graphics.FillPath(br, path);
        }

       
    }
    }

```

ผลการทดลอง


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/6.JPG)
###แบบทดสอบ 
ให้เลื่อนจุดศูนย์กลางและปรับเปลี่ยนสี ให้ได้รูปดังนี้
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-9.png">
</p>


![](https://github.com/NAPHARAT/LAB-11/blob/master/imgs/7.JPG)
