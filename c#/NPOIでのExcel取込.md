# NPOIでのExcel取込

主題どおりNPOIでExcelを取り込む方法

```C#
using NPOI.SS.UserModel;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Excel使用テスト.Sharp {
    public partial class Form1 : Form {
        public Form1()
        {
            InitializeComponent();
        }

        private void bt_NPOI取込_Click(object sender, EventArgs e)
        {
            try {

                // Excelファイルの取込 //
                var npoiBook = WorkbookFactory.Create("ファイルの場所");

                // シートを取得 //
                var npoisheet = npoiBook.GetSheet("シート名");
　　　　　　　　　
　　　　　　　　　// 行数と列数を指定してセルの値を取得 //
                string strValue = NpoiGetCellValue(npoisheet, 4, 1);

                MessageBox.Show(strValue);

            }

            catch(Exception ex) {

                MessageBox.Show(ex.Message);

            }


        }

        //*************************************************************
        // セルから値を取り出す
        //*************************************************************
        private string NpoiGetCellValue(ISheet sheet, int introw, int intcol)
        {
            string strResult = "";

            IRow row;

            ICell cell;

            if (sheet.GetRow(introw) == null) {

                // Nullだとエラーになるため回避 //
                row = sheet.CreateRow(introw);
            }

            // 行取得 //
            row = sheet.GetRow(introw);

            if(row.GetCell(intcol) == null) {

                // Nullだとエラーになるため回避 //
                cell = row.CreateCell(intcol);
            }

            // 行から列を取得 //
            cell = row.GetCell(intcol);

            // セルの書式 //
            switch (cell.CellType) {

                case CellType.String:
                    strResult = cell.StringCellValue;
                    break;

                case CellType.Numeric:
                    strResult = cell.NumericCellValue.ToString();
                    break;

                default:
                    strResult = "値なし";
                    break;

            }

            return strResult;
        }
    }
}
```

個人的にはMicrosoft.Office.Interop.ExcelよりはNOPIを使いたい

### 参考

[【C\#】NPOIならExcel操作が簡単にできる！使い方まとめ \| 侍エンジニアブログ](https://www.sejuku.net/blog/100771)