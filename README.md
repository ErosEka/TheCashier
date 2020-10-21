# TheCashier
Aplikasi untuk kemudahan kasir untuk menginputkan barang atau jasa yang dibeli dan menjumlahkan total harganya.

Penggunaan Single Reponsibility terdapat pada class Calculator. Class ini digunakan untuk memproses inputan dari user untuk segera ditambahkan dan dijumlahkan harganya.

    public void AddItem(Item item)
    {
        this.listItem.Add(item);
        this.total += item.getSubtotal();
    }
    
Pada MainWindow() diatas adalah penginisialisasian untuk calculator mengambil dari Class Calculator untuk menampilkan listBox yang ada didalamnya.

    public MainWindow()
    {
        InitializeComponent();
        calculator = new Calculator();
        listBox.ItemsSource = calculator.getListItem();
    }
    
Untuk yang bawah ini adalah penginisialisasian button untuk proses penginputan dan penjumlahan. Setelah semua bahan telah diinputkan akan dibaca dan akan langsung diambil oleh class item dan dilanjutkan pada class calculator. Disana akan diproses dan ditambahkan, akhir dari proses adalah ketika item sudah tertampil di listbox, dimana listbox diambil dari Calculator.cs.

        private void AddButton_Click(object sender, RoutedEventArgs e)
        {

            string title = itemNameBox.Text;
            int quantity = int.Parse(quantityBox.Text);
            string type = typeBox.Text;
            double price = double.Parse(priceBox.Text);


            Item item = new Item(new Random().Next(), title, quantity, type, price);
            calculator.addItem(item);
            double total = calculator.getTotal();

            totalLabel.Content = String.Format("Rp. {0}", total);

            listBox.Items.Refresh();
        }
