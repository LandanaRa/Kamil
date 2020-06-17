# Сайт для приложения Текстовый редактор
 ## Код программы

 - using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;
using System.Windows.Forms;
using Microsoft.Win32;
using System.Text.RegularExpressions;
using Microsoft.Office.Interop;
namespace TextoviyRedactor
{
    public partial class MainForm : Form
    {
        Form InfoForm = new Form();
        public MainForm()
        {
            InitializeComponent();
            colorDialog1.FullOpen = true;
            colorDialog1.Color = this.BackColor;
        }
        private void НовыйToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("Хотите сохранить файл?", "Новый документ", MessageBoxButtons.OKCancel) == DialogResult.Cancel)
            {
                richTextBox1.Clear();
            }
            else
            {
                SaveFileDialog saveFD = new SaveFileDialog();

                string saved_file = "";

                saveFD.InitialDirectory = "C:\\Users\\4rake\\Desktop\\File Text Reader Phenix";
                saveFD.Title = "Save a Text File";
                saveFD.FileName = "";

                saveFD.Filter = "Text Files|*.txt|Word Documents|*.doc|Exel|*.xls|PDF|*.Pdf";

                if (saveFD.ShowDialog() != DialogResult.Cancel)
                {

                    saved_file = saveFD.FileName;
                    richTextBox1.SaveFile(saved_file, RichTextBoxStreamType.PlainText);
                    MessageBox.Show("Файл был сохранен!", "Успешно", MessageBoxButtons.OK, MessageBoxIcon.Information);

                }
            }
        }

        private void ОткрытьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            OpenFileDialog openFileDialog = new OpenFileDialog();
            if (openFileDialog.ShowDialog() == DialogResult.OK)
            {
                richTextBox1.Text = File.ReadAllText(openFileDialog.FileName);
            }
        }

        private void СохранитьКакToolStripMenuItem_Click(object sender, EventArgs e)
        {
            
                SaveFileDialog saveFD = new SaveFileDialog();

                string saved_file = "";

                saveFD.InitialDirectory = "C:\\Users\\4rake\\Desktop\\File Text Reader Phenix";
                saveFD.Title = "Save a Text File";
                saveFD.FileName = "";

                saveFD.Filter = "Text Files|*.txt|Word Documents|*.doc|Exel|*.xls|PDF|*.Pdf";

                if (saveFD.ShowDialog() != DialogResult.Cancel)
                {

                    saved_file = saveFD.FileName;
                    richTextBox1.SaveFile(saved_file, RichTextBoxStreamType.PlainText);
                    MessageBox.Show("Файл был сохранен!", "Успешно", MessageBoxButtons.OK, MessageBoxIcon.Information);

                }
        }

        private void ЗаакрытьФайлToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("Хотите сохранить файл?", "Закрыть", MessageBoxButtons.OKCancel) == DialogResult.Cancel)
            {
                richTextBox1.Clear();
            }
            else
            {
                SaveFileDialog saveFD = new SaveFileDialog();

                string saved_file = "";

                saveFD.InitialDirectory = "C:\\Users\\User\\Desktop\\File Text Reader Phenix";
                saveFD.Title = "Save a Text File";
                saveFD.FileName = "";

                saveFD.Filter = "Text Files|*.txt|Word Documents|*.doc|Exel|*.xls|PDF|*.Pdf";

                if (saveFD.ShowDialog() != DialogResult.Cancel)
                {

                    saved_file = saveFD.FileName;
                    richTextBox1.SaveFile(saved_file, RichTextBoxStreamType.PlainText);
                    MessageBox.Show("Файл был сохранен!", "Успешно", MessageBoxButtons.OK, MessageBoxIcon.Information);

                }
            }
        }

        private void ВыходИзПрограммыToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (MessageBox.Show("Хотите сохранить файл?", "Закрыть", MessageBoxButtons.OKCancel) == DialogResult.Cancel)
            {
                Application.Exit();
            }
            else
            {
                SaveFileDialog saveFD = new SaveFileDialog();

                string saved_file = "";

                saveFD.InitialDirectory = "C:\\Users\\User\\Desktop\\File Text Reader Phenix";
                saveFD.Title = "Save a Text File";
                saveFD.FileName = "";

                saveFD.Filter = "Text Files|*.txt|Word Documents|*.doc|Exel|*.xls|PDF|*.Pdf";

                if (saveFD.ShowDialog() != DialogResult.Cancel)
                {

                    saved_file = saveFD.FileName;
                    richTextBox1.SaveFile(saved_file, RichTextBoxStreamType.PlainText);
                    MessageBox.Show("Файл был сохранен!", "Успешно", MessageBoxButtons.OK, MessageBoxIcon.Information);

                }
            }
        }

        private void ПолныйЭкранToolStripMenuItem_Click(object sender, EventArgs e)
        {
            this.MaximizeBox = true;
            this.WindowState = FormWindowState.Maximized;
        }

        private void СвернутьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            this.MinimizeBox = true;
        }

        private void УбратьПолныйЭкранToolStripMenuItem_Click(object sender, EventArgs e)
        {
            MaximizeBox = false;
        }

        private void ИзменитьРамкуToolStripMenuItem_Click(object sender, EventArgs e)
        {
            MinimizeBox = false;
        }

        private void ВырезатьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.Cut();
        }

        private void КопироватьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.Copy();
        }

        private void ВставитьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.Paste();
        }

        private void ОтменитьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.Undo();
        }

        private void ОПрограммеToolStripMenuItem1_Click(object sender, EventArgs e)
        {
            InfoForm.Height = 175;
            InfoForm.Width = 250;
            InfoForm.FormBorderStyle = FormBorderStyle.None;
            InfoForm.StartPosition = FormStartPosition.CenterScreen;
            InfoForm.BackColor = Color.Gray;
            Panel panel = new Panel();
            panel.Dock = DockStyle.Bottom;
            panel.Height = 25;
            InfoForm.Controls.Add(panel);
            Button button = new Button();
            Label label = new Label();
            label.Dock = DockStyle.Fill;
            label.ForeColor = Color.White;
            label.Text = "Текстовый реадктор. " +
                "Используется в качестве учебных средств. " +
                "\n\n\nВ возможность входит: " +
                "работа с файлами форматов " +
                "(txt, Microsoft Word, Microsoft Exel, PDF). " +
                "Построение диаграмм символов. \n\n\n\n " +
                "Разработчик: Пузанов Алексей Борисович ";
            button.FlatStyle = FlatStyle.Flat;
            button.ForeColor = Color.White;
            button.Text = "Закрыть";
            button.Click += button_click;
            panel.Controls.Add(button);
            InfoForm.Controls.Add(label);
            InfoForm.ShowDialog();
        }
        private void button_click(object sender, EventArgs e)
        {
            InfoForm.Close();
        }

        private void RichTextBox1_TextChanged(object sender, EventArgs e)
        {
            //if (colorDialog1.ShowDialog() == DialogResult.Cancel)
            //    return;
            //this.BackColor = colorDialog1.Color;;
        }

        private void ToolStripButton2_Click(object sender, EventArgs e)
        {
            if (richTextBox1.SelectionFont.Style == FontStyle.Bold)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Italic | FontStyle.Bold);
            if (richTextBox1.SelectionFont.Style == FontStyle.Underline)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Italic | FontStyle.Underline);
            if (richTextBox1.SelectionFont.Style == FontStyle.Regular)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Italic);
            else
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Italic | FontStyle.Bold | FontStyle.Underline);
            richTextBox1.Select();
        }

        private void ToolStripButton1_Click(object sender, EventArgs e)
        {
            if (richTextBox1.SelectionFont.Style == FontStyle.Italic)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Bold | FontStyle.Italic);
            if (richTextBox1.SelectionFont.Style == FontStyle.Underline)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Bold | FontStyle.Underline);
            if (richTextBox1.SelectionFont.Style == FontStyle.Regular)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Bold);
            else
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Bold | FontStyle.Italic | FontStyle.Underline);
            richTextBox1.Select();
        }

        private void ToolStripButton3_Click(object sender, EventArgs e)
        {
            if (richTextBox1.SelectionFont.Style == FontStyle.Bold)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Underline | FontStyle.Bold);
            if (richTextBox1.SelectionFont.Style == FontStyle.Italic)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Underline | FontStyle.Italic);
            if (richTextBox1.SelectionFont.Style == FontStyle.Regular)
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Underline);
            else
                richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont, FontStyle.Underline | FontStyle.Bold | FontStyle.Italic);
            richTextBox1.Select();
        }

        private void ToolStripButton4_Click(object sender, EventArgs e)
        {
            richTextBox1.SelectionAlignment = HorizontalAlignment.Left;
        }

        private void ToolStripButton5_Click(object sender, EventArgs e)
        {
            richTextBox1.SelectionAlignment = HorizontalAlignment.Center;
        }

        private void ToolStripButton6_Click(object sender, EventArgs e)
        {
            richTextBox1.SelectionAlignment = HorizontalAlignment.Right;
        }

        private void ToolStripButton10_Click(object sender, EventArgs e)
        {
            FontDialog fd = new FontDialog();
            if (fd.ShowDialog() == DialogResult.OK)
                richTextBox1.Font = fd.Font;
        }

        private void ЗаменитьToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.Text = richTextBox1.Text.Replace(richTextBox1.SelectedText, textBox1.Text);    
        }

        private void НайтиToolStripMenuItem_Click(object sender, EventArgs e)
        {
  
        }

        private void НайтиToolStripMenuItem1_Click(object sender, EventArgs e)
        {
            richTextBox1.Find(textBox3.Text, RichTextBoxFinds.MatchCase);
        }

        private void ВыделитьВсеToolStripMenuItem_Click(object sender, EventArgs e)
        {
            richTextBox1.SelectAll();
        }
        private void RichTextBox1_KeyDown(object sender, KeyEventArgs e)
        {
            label5.Text = "Колличество символов: " + richTextBox1.TextLength.ToString();
        }

        private void НастройкаИнтерфейсаToolStripMenuItem_Click(object sender, EventArgs e)
        {
            if (colorDialog1.ShowDialog() == DialogResult.Cancel)
                return;
            this.BackColor = colorDialog1.Color;
        }

    }
}
