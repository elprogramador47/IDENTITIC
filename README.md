# IDENTITIC
solo facu moreno lo entiende 
namespace IDENTITIC_PRINCIPAL
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        [DllImport("user32.DLL", EntryPoint = "ReleaseCapture")]
        private extern static void ReleaseCapture();
        [DllImport("user32.DLL", EntryPoint = "SendMessage")]

        private extern static void SendMessage(System.IntPtr hWnd, int wMsg, int wParam, int lParam);

        

        
        

      

        private void iconcerrar_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }

       
        private void iconminimizar_Click(object sender, EventArgs e)
        {
            this.WindowState = FormWindowState.Minimized;
        }

        private void BarradeTitulo_MouseDown(object sender, MouseEventArgs e)
        {
            ReleaseCapture();
            SendMessage(this.Handle, 0x112, 0xf012, 0);

        }

     

        private void AbrirFormInPanel(object formHijo)
        {
            if (this.panelcontenedor.Controls.Count > 0)
                this.panelcontenedor.Controls.RemoveAt(0);
            Form fh = formHijo as Form;
            fh.TopLevel = false;
            fh.FormBorderStyle = FormBorderStyle.None;
            fh.Dock = DockStyle.Fill;
            this.panelcontenedor.Controls.Add(fh);
            this.panelcontenedor.Tag = fh;
            fh.Show();
        }




        private void horayfecha_Tick(object sender, EventArgs e)
        {
            lblhora.Text = DateTime.Now.ToLongTimeString();
            lblFecha.Text = DateTime.Now.ToLongDateString();
        }

        private void panelcontenedor_Paint(object sender, PaintEventArgs e)
        {

        }

        private void btnproducto_Click(object sender, EventArgs e)
        {

            AbrirFormInPanel(new Acceder());
            lblFecha.Visible = false;
            lblhora.Visible = false;

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }
    }
}
