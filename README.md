<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perpustakaan Pintar - Sistem Manajemen Buku</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --primary: #9b59b6;
            --primary-light: #be90d4;
            --primary-dark: #8e44ad;
            --secondary: #8e44ad;
            --accent: #a569bd;
            --danger: #e74c3c;
            --light: #f5eef8;
            --dark: #2c3e50;
            --success: #2ecc71;
            --warning: #f39c12;
            --text: #4a235a;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #faf5ff;
            color: var(--text);
        }
        
        .header {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(155, 89, 182, 0.2);
        }
        
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        
        .card {
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(155, 89, 182, 0.1);
            margin-bottom: 2rem;
            overflow: hidden;
            border: 1px solid #e8daef;
        }
        
        .card-header {
            background: linear-gradient(to right, var(--primary), var(--accent));
            color: white;
            padding: 1rem 1.5rem;
            font-size: 1.2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .card-body {
            padding: 1.5rem;
        }
        
        .form-group {
            margin-bottom: 1.3rem;
        }
        
        label {
            display: block;
            margin-bottom: 0.6rem;
            font-weight: 600;
            color: var(--primary-dark);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #d2b4de;
            border-radius: 6px;
            font-size: 1rem;
            transition: all 0.3s;
            background-color: var(--light);
        }
        
        input:focus, select:focus, textarea:focus {
            border-color: var(--accent);
            outline: none;
            box-shadow: 0 0 0 3px rgba(155, 89, 182, 0.2);
            background-color: white;
        }
        
        .btn {
            display: inline-block;
            padding: 0.8rem 1.6rem;
            border: none;
            border-radius: 6px;
            font-size: 1rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        
        .btn-primary {
            background: linear-gradient(to right, var(--primary), var(--accent));
            color: white;
            box-shadow: 0 2px 8px rgba(155, 89, 182, 0.3);
        }
        
        .btn-primary:hover {
            background: linear-gradient(to right, var(--primary-dark), var(--secondary));
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(155, 89, 182, 0.4);
        }
        
        .btn-danger {
            background: linear-gradient(to right, var(--danger), #c0392b);
            color: white;
            box-shadow: 0 2px 8px rgba(231, 76, 60, 0.3);
        }
        
        .btn-danger:hover {
            background: linear-gradient(to right, #c0392b, var(--danger));
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(231, 76, 60, 0.4);
        }
        
        .btn-warning {
            background: linear-gradient(to right, var(--warning), #e67e22);
            color: white;
            box-shadow: 0 2px 8px rgba(241, 196, 15, 0.3);
        }
        
        .btn-warning:hover {
            background: linear-gradient(to right, #e67e22, var(--warning));
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(241, 196, 15, 0.4);
        }
        
        .btn-secondary {
            background: linear-gradient(to right, #7f8c8d, #95a5a6);
            color: white;
            box-shadow: 0 2px 8px rgba(127, 140, 141, 0.3);
        }
        
        .btn-secondary:hover {
            background: linear-gradient(to right, #95a5a6, #7f8c8d);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(127, 140, 141, 0.4);
        }
        
        .form-row {
            display: flex;
            gap: 1.2rem;
            margin-bottom: 1.2rem;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        .table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1.5rem;
        }
        
        .table th, .table td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #e8daef;
        }
        
        .table th {
            background-color: var(--light);
            font-weight: 600;
            color: var(--primary-dark);
        }
        
        .table tr:hover {
            background-color: rgba(155, 89, 182, 0.05);
        }
        
        .action-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1.1rem;
            margin: 0 0.4rem;
            color: var(--dark);
            transition: all 0.3s;
            padding: 0.5rem;
            border-radius: 50%;
        }
        
        .action-btn.edit {
            color: var(--primary);
            background-color: rgba(155, 89, 182, 0.1);
        }
        
        .action-btn.delete {
            color: var(--danger);
            background-color: rgba(231, 76, 60, 0.1);
        }
        
        .action-btn.stok {
            color: var(--warning);
            background-color: rgba(241, 196, 15, 0.1);
        }
        
        .action-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        .stok-indicator {
            display: inline-block;
            padding: 0.4rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            min-width: 70px;
            text-align: center;
        }
        
        .stok-tinggi {
            background-color: rgba(46, 204, 113, 0.2);
            color: #27ae60;
        }
        
        .stok-sedang {
            background-color: rgba(241, 196, 15, 0.2);
            color: #f39c12;
        }
        
        .stok-rendah {
            background-color: rgba(231, 76, 60, 0.2);
            color: #c0392b;
        }
        
        .footer {
            text-align: center;
            padding: 1.5rem;
            background-color: var(--dark);
            color: white;
            margin-top: 3rem;
            font-size: 0.9rem;
        }
        
        .hidden {
            display: none;
        }
        
        .tabs {
            display: flex;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid #e8daef;
        }
        
        .tab {
            padding: 0.8rem 1.8rem;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
            font-weight: 500;
            color: var(--text);
            position: relative;
        }
        
        .tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary-dark);
            font-weight: 600;
        }
        
        .tab:hover {
            color: var(--primary);
            background-color: rgba(155, 89, 182, 0.05);
        }
        
        .tab-content {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Modal Edit */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.4);
        }
        
        .modal-content {
            background-color: white;
            margin: 5% auto;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.2);
            width: 80%;
            max-width: 600px;
            animation: modalFadeIn 0.3s;
        }
        
        @keyframes modalFadeIn {
            from { opacity: 0; transform: translateY(-50px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid #e8daef;
        }
        
        .modal-title {
            color: var(--primary-dark);
            margin: 0;
            font-size: 1.5rem;
        }
        
        .close-modal {
            color: #aaa;
            font-size: 1.8rem;
            font-weight: bold;
            cursor: pointer;
            transition: color 0.3s;
        }
        
        .close-modal:hover {
            color: var(--danger);
        }
        
        .modal-footer {
            display: flex;
            justify-content: flex-end;
            gap: 1rem;
            margin-top: 1.5rem;
            padding-top: 1rem;
            border-top: 1px solid #e8daef;
        }
        
        /* Book Cover Preview */
        .cover-preview-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .cover-preview {
            width: 150px;
            height: 200px;
            border: 2px dashed #d2b4de;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            margin-bottom: 1rem;
            background-color: #f9f9f9;
        }
        
        .cover-preview img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }
        
        .cover-preview-placeholder {
            text-align: center;
            color: #8e44ad;
            font-size: 3rem;
        }
        
        .cover-upload-label {
            display: inline-block;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s;
            background-color: rgba(155, 89, 182, 0.1);
            color: var(--primary-dark);
            text-align: center;
        }
        
        .cover-upload-label:hover {
            background-color: rgba(155, 89, 182, 0.2);
        }
        
        .cover-upload-btn {
            display: none;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .form-row {
                flex-direction: column;
                gap: 0;
            }
            
            .tabs {
                flex-direction: column;
                border-bottom: none;
            }
            
            .tab {
                border-bottom: none;
                border-left: 3px solid transparent;
            }
            
            .tab.active {
                border-bottom: none;
                border-left: 3px solid var(--primary);
            }
            
            .modal-content {
                width: 95%;
                margin: 10% auto;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>PERPUSTAKAAN PINTAR</h1>
        <p>Sistem Manajemen Koleksi Buku Digital</p>
    </div>
    
    <div class="container">
        <div class="tabs">
            <div class="tab active" onclick="openTab('inputTab')">
                <i class="fas fa-book-medical"></i> Input Buku
            </div>
            <div class="tab" onclick="openTab('dataTab')">
                <i class="fas fa-book-open"></i> Data Buku
            </div>
        </div>
        
        <div id="inputTab" class="tab-content active">
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-plus-circle"></i> Formulir Input Buku Baru</span>
                </div>
                <div class="card-body">
                    <form id="formStokBuku">
                        <div class="cover-preview-container">
                            <div class="cover-preview" id="coverPreview">
                                <div class="cover-preview-placeholder">
                                    <i class="fas fa-book"></i>
                                </div>
                            </div>
                            <label for="fileUpload" class="cover-upload-label">
                                <i class="fas fa-upload"></i> Unggah Gambar Sampul
                            </label>
                            <input type="file" id="fileUpload" class="cover-upload-btn" accept="image/*">
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="judulBuku">Judul Buku <span class="required">*</span></label>
                                <input type="text" id="judulBuku" name="judulBuku" required placeholder="Masukkan judul lengkap buku">
                            </div>
                            <div class="form-group">
                                <label for="pengarang">Pengarang <span class="required">*</span></label>
                                <input type="text" id="pengarang" name="pengarang" required placeholder="Nama pengarang">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="penerbit">Penerbit <span class="required">*</span></label>
                                <input type="text" id="penerbit" name="penerbit" required placeholder="Nama penerbit">
                            </div>
                            <div class="form-group">
                                <label for="tahunTerbit">Tahun Terbit <span class="required">*</span></label>
                                <input type="number" id="tahunTerbit" name="tahunTerbit" min="1900" max="2099" required placeholder="Tahun terbit">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="kategori">Kategori <span class="required">*</span></label>
                                <select id="kategori" name="kategori" required>
                                    <option value="">Pilih Kategori</option>
                                    <option value="Fiksi">Fiksi</option>
                                    <option value="Non-Fiksi">Non-Fiksi</option>
                                    <option value="Pelajaran">Pelajaran</option>
                                    <option value="Referensi">Referensi</option>
                                    <option value="Anak-anak">Anak-anak</option>
                                    <option value="Teknologi">Teknologi</option>
                                    <option value="Sains">Sains</option>
                                    <option value="Sejarah">Sejarah</option>
                                    <option value="Agama">Agama</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="stok">Jumlah Stok <span class="required">*</span></label>
                                <input type="number" id="stok" name="stok" min="0" required placeholder="Jumlah buku yang tersedia">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="deskripsi">Deskripsi Buku</label>
                            <textarea id="deskripsi" name="deskripsi" rows="4" placeholder="Masukkan deskripsi singkat tentang buku"></textarea>
                        </div>
                        
                        <div class="form-group" style="text-align: right;">
                            <button type="reset" class="btn btn-danger" id="resetFormBtn">
                                <i class="fas fa-undo"></i> Reset
                            </button>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-save"></i> Simpan Buku
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
        
        <div id="dataTab" class="tab-content">
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-book"></i> Daftar Stok Buku</span>
                    <div>
                        <input type="text" id="searchInput" placeholder="Cari judul/pengarang..." style="padding: 0.6rem; border-radius: 6px; border: 1px solid #d2b4de; min-width: 250px;">
                    </div>
                </div>
                <div class="card-body">
                    <table class="table">
                        <thead>
                            <tr>
                                <th>No</th>
                                <th>Judul Buku</th>
                                <th>Pengarang</th>
                                <th>Penerbit</th>
                                <th>Tahun</th>
                                <th>Kategori</th>
                                <th>Stok</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="bukuTableBody">
                            <!-- Data buku akan dimasukkan di sini oleh JavaScript -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal Edit Buku -->
    <div id="editModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Edit Detail Buku</h3>
                <span class="close-modal">&times;</span>
            </div>
            <form id="editBukuForm">
                <input type="hidden" id="editBukuId">
                <div class="cover-preview-container">
                    <div class="cover-preview" id="editCoverPreview">
                        <div class="cover-preview-placeholder">
                            <i class="fas fa-book"></i>
                        </div>
                    </div>
                    <label for="editFileUpload" class="cover-upload-label">
                        <i class="fas fa-upload"></i> Unggah Gambar Sampul
                    </label>
                    <input type="file" id="editFileUpload" class="cover-upload-btn" accept="image/*">
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="editJudul">Judul Buku <span class="required">*</span></label>
                        <input type="text" id="editJudul" required>
                    </div>
                    <div class="form-group">
                        <label for="editPengarang">Pengarang <span class="required">*</span></label>
                        <input type="text" id="editPengarang" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="editPenerbit">Penerbit <span class="required">*</span></label>
                        <input type="text" id="editPenerbit" required>
                    </div>
                    <div class="form-group">
                        <label for="editTahun">Tahun Terbit <span class="required">*</span></label>
                        <input type="number" id="editTahun" min="1900" max="2099" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="editKategori">Kategori <span class="required">*</span></label>
                        <select id="editKategori" required>
                            <option value="">Pilih Kategori</option>
                            <option value="Fiksi">Fiksi</option>
                            <option value="Non-Fiksi">Non-Fiksi</option>
                            <option value="Pelajaran">Pelajaran</option>
                            <option value="Referensi">Referensi</option>
                            <option value="Anak-anak">Anak-anak</option>
                            <option value="Teknologi">Teknologi</option>
                            <option value="Sains">Sains</option>
                            <option value="Sejarah">Sejarah</option>
                            <option value="Agama">Agama</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="editStok">Jumlah Stok <span class="required">*</span></label>
                        <input type="number" id="editStok" min="0" required>
                    </div>
                </div>
                <div class="form-group">
                    <label for="editDeskripsi">Deskripsi Buku</label>
                    <textarea id="editDeskripsi" rows="4"></textarea>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-danger" id="cancelEdit">Batal</button>
                    <button type="submit" class="btn btn-primary">Simpan Perubahan</button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Modal Kelola Stok -->
    <div id="stokModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Kelola Stok Buku</h3>
                <span class="close-modal">&times;</span>
            </div>
            <form id="stokForm">
                <input type="hidden" id="stokBukuId">
                <div class="form-group">
                    <label for="stokJudul">Judul Buku</label>
                    <input type="text" id="stokJudul" readonly>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label for="stokSaatIni">Stok Saat Ini</label>
                        <input type="number" id="stokSaatIni" readonly>
                    </div>
                    <div class="form-group">
                        <label for="stokAksi">Aksi <span class="required">*</span></label>
                        <select id="stokAksi" required>
                            <option value="">Pilih Aksi</option>
                            <option value="tambah">Tambah Stok</option>
                            <option value="kurang">Kurangi Stok</option>
                        </select>
                    </div>
                </div>
                <div class="form-group">
                    <label for="stokJumlah">Jumlah <span class="required">*</span></label>
                    <input type="number" id="stokJumlah" min="1" value="1" required>
                </div>
                <div class="form-group">
                    <label for="stokCatatan">Catatan</label>
                    <textarea id="stokCatatan" rows="3" placeholder="Masukkan catatan perubahan stok"></textarea>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-danger" id="cancelStok">Batal</button>
                    <button type="submit" class="btn btn-primary">Simpan Perubahan</button>
                </div>
            </form>
        </div>
    </div>
    
    <div class="footer">
        &copy; 2023 Perpustakaan Pintar - Sistem Manajemen Koleksi Buku Digital | Versi 3.0
    </div>
    
    <script>
        // Data buku (simulasi database)
        let bukuData = [
            {
                id: 1,
                judul: "Laskar Pelangi",
                pengarang: "Andrea Hirata",
                penerbit: "Bentang Pustaka",
                tahun: 2005,
                kategori: "Fiksi",
                stok: 15,
                deskripsi: "Novel tentang persahabatan dan pendidikan di Belitung",
                sampul: null,
                stokHistory: []
            },
            {
                id: 2,
                judul: "Bumi Manusia",
                pengarang: "Pramoedya Ananta Toer",
                penerbit: "Hasta Mitra",
                tahun: 1980,
                kategori: "Fiksi",
                stok: 8,
                deskripsi: "Bagian pertama dari Tetralogi Buru yang bercerita tentang Minke",
                sampul: null,
                stokHistory: []
            },
            {
                id: 3,
                judul: "Filosofi Teras",
                pengarang: "Henry Manampiring",
                penerbit: "Kompas",
                tahun: 2018,
                kategori: "Non-Fiksi",
                stok: 3,
                deskripsi: "Filsafat Stoikisme untuk kehidupan modern",
                sampul: null,
                stokHistory: []
            }
        ];
        
        // Fungsi untuk menampilkan data buku ke tabel
        function renderBukuTable(data = bukuData) {
            const tableBody = document.getElementById('bukuTableBody');
            tableBody.innerHTML = '';
            
            data.forEach((buku, index) => {
                const row = document.createElement('tr');
                
                // Tentukan kelas stok berdasarkan jumlah
                let stokClass = 'stok-tinggi';
                if (buku.stok < 5) stokClass = 'stok-rendah';
                else if (buku.stok < 10) stokClass = 'stok-sedang';
                
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td><strong>${buku.judul}</strong></td>
                    <td>${buku.pengarang}</td>
                    <td>${buku.penerbit}</td>
                    <td>${buku.tahun}</td>
                    <td><span style="background-color: rgba(155, 89, 182, 0.1); padding: 0.3rem 0.6rem; border-radius: 4px; color: var(--primary-dark);">${buku.kategori}</span></td>
                    <td><span class="stok-indicator ${stokClass}">${buku.stok} buku</span></td>
                    <td>
                        <button class="action-btn edit" onclick="openEditModal(${buku.id})" title="Edit">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="action-btn stok" onclick="openStokModal(${buku.id})" title="Kelola Stok">
                            <i class="fas fa-boxes"></i>
                        </button>
                        <button class="action-btn delete" onclick="hapusBuku(${buku.id})" title="Hapus">
                            <i class="fas fa-trash-alt"></i>
                        </button>
                    </td>
                `;
                
                tableBody.appendChild(row);
            });
        }
        
        // Fungsi untuk menampilkan preview gambar sampul
        function displayCoverPreview(file, previewElementId) {
            const preview = document.getElementById(previewElementId);
            preview.innerHTML = '';
            
            if (file) {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    preview.appendChild(img);
                }
                
                reader.readAsDataURL(file);
            } else {
                const placeholder = document.createElement('div');
                placeholder.className = 'cover-preview-placeholder';
                placeholder.innerHTML = '<i class="fas fa-book"></i>';
                preview.appendChild(placeholder);
            }
        }
        
        // Fungsi untuk membuka modal edit buku
        function openEditModal(id) {
            const buku = bukuData.find(b => b.id === id);
            if (!buku) return;
            
            // Isi form edit dengan data buku
            document.getElementById('editBukuId').value = buku.id;
            document.getElementById('editJudul').value = buku.judul;
            document.getElementById('editPengarang').value = buku.pengarang;
            document.getElementById('editPenerbit').value = buku.penerbit;
            document.getElementById('editTahun').value = buku.tahun;
            document.getElementById('editKategori').value = buku.kategori;
            document.getElementById('editStok').value = buku.stok;
            document.getElementById('editDeskripsi').value = buku.deskripsi;
            
            // Tampilkan sampul buku jika ada
            const editCoverPreview = document.getElementById('editCoverPreview');
            editCoverPreview.innerHTML = '';
            
            if (buku.sampul) {
                const img = document.createElement('img');
                img.src = buku.sampul;
                editCoverPreview.appendChild(img);
            } else {
                const placeholder = document.createElement('div');
                placeholder.className = 'cover-preview-placeholder';
                placeholder.innerHTML = '<i class="fas fa-book"></i>';
                editCoverPreview.appendChild(placeholder);
            }
            
            // Reset file input
            document.getElementById('editFileUpload').value = '';
            
            // Tampilkan modal
            document.getElementById('editModal').style.display = 'block';
        }
        
        // Fungsi untuk menyimpan perubahan edit buku
        function simpanEditBuku(event) {
            event.preventDefault();
            
            const id = parseInt(document.getElementById('editBukuId').value);
            const bukuIndex = bukuData.findIndex(b => b.id === id);
            
            if (bukuIndex === -1) return;
            
            // Cek apakah ada file gambar baru yang diunggah
            const fileUpload = document.getElementById('editFileUpload');
            let newCover = bukuData[bukuIndex].sampul;
            
            if (fileUpload.files.length > 0) {
                const file = fileUpload.files[0];
                const reader = new FileReader();
                reader.onload = function(e) {
                    newCover = e.target.result;
                    updateBookData();
                };
                reader.readAsDataURL(file);
            } else {
                updateBookData();
            }
            
            function updateBookData() {
                // Update data buku
                bukuData[bukuIndex] = {
                    ...bukuData[bukuIndex],
                    judul: document.getElementById('editJudul').value,
                    pengarang: document.getElementById('editPengarang').value,
                    penerbit: document.getElementById('editPenerbit').value,
                    tahun: parseInt(document.getElementById('editTahun').value),
                    kategori: document.getElementById('editKategori').value,
                    stok: parseInt(document.getElementById('editStok').value),
                    deskripsi: document.getElementById('editDeskripsi').value,
                    sampul: newCover
                };
                
                // Render ulang tabel
                renderBukuTable();
                
                // Tutup modal
                document.getElementById('editModal').style.display = 'none';
                
                alert('Data buku berhasil diperbarui!');
            }
        }
        
        // Fungsi untuk membuka modal kelola stok
        function openStokModal(id) {
            const buku = bukuData.find(b => b.id === id);
            if (!buku) return;
            
            document.getElementById('stokBukuId').value = buku.id;
            document.getElementById('stokJudul').value = buku.judul;
            document.getElementById('stokSaatIni').value = buku.stok;
            document.getElementById('stokJumlah').value = 1;
            document.getElementById('stokCatatan').value = '';
            document.getElementById('stokAksi').value = '';
            
            document.getElementById('stokModal').style.display = 'block';
        }
        
        // Fungsi untuk menutup modal
        function closeModal() {
            document.getElementById('editModal').style.display = 'none';
            document.getElementById('stokModal').style.display = 'none';
        }
        
        // Fungsi untuk menyimpan perubahan stok
        function simpanPerubahanStok(event) {
            event.preventDefault();
            
            const id = parseInt(document.getElementById('stokBukuId').value);
            const aksi = document.getElementById('stokAksi').value;
            const jumlah = parseInt(document.getElementById('stokJumlah').value);
            const catatan = document.getElementById('stokCatatan').value;
            
            const bukuIndex = bukuData.findIndex(b => b.id === id);
            if (bukuIndex === -1) return;
            
            const buku = bukuData[bukuIndex];
            const stokAwal = buku.stok;
            let stokAkhir = stokAwal;
            let jumlahPerubahan = 0;
            
            // Validasi
            if (!aksi) {
                alert('Pilih aksi terlebih dahulu!');
                return;
            }
            
            if (isNaN(jumlah) || jumlah <= 0) {
                alert('Jumlah harus lebih dari 0!');
                return;
            }
            
            // Proses perubahan stok
            if (aksi === 'tambah') {
                stokAkhir = stokAwal + jumlah;
                jumlahPerubahan = jumlah;
            } 
            else if (aksi === 'kurang') {
                if (jumlah > stokAwal) {
                    alert('Jumlah pengurangan tidak boleh lebih dari stok saat ini!');
                    return;
                }
                stokAkhir = stokAwal - jumlah;
                jumlahPerubahan = -jumlah;
            }
            
            // Update stok buku
            bukuData[bukuIndex].stok = stokAkhir;
            
            // Tambahkan ke history
            bukuData[bukuIndex].stokHistory.push({
                tanggal: new Date().toISOString(),
                aksi: aksi,
                jumlah: Math.abs(jumlahPerubahan),
                stokAwal: stokAwal,
                stokAkhir: stokAkhir,
                catatan: catatan || `Stok di${aksi === 'tambah' ? 'tambah' : 'kurangi'}`
            });
            
            // Render ulang tabel
            renderBukuTable();
            
            // Tutup modal
            closeModal();
            
            alert('Stok buku berhasil diperbarui!');
        }
        
        // Fungsi untuk menghapus buku
        function hapusBuku(id) {
            if (confirm('Apakah Anda yakin ingin menghapus buku ini?')) {
                bukuData = bukuData.filter(buku => buku.id !== id);
                renderBukuTable();
                alert('Buku berhasil dihapus!');
            }
        }
        
        // Fungsi untuk menambahkan buku baru
        function tambahBuku(event) {
            event.preventDefault();
            
            const judul = document.getElementById('judulBuku').value;
            const pengarang = document.getElementById('pengarang').value;
            const penerbit = document.getElementById('penerbit').value;
            const tahun = parseInt(document.getElementById('tahunTerbit').value);
            const kategori = document.getElementById('kategori').value;
            const stok = parseInt(document.getElementById('stok').value);
            const deskripsi = document.getElementById('deskripsi').value;
            
            // Validasi
            if (!judul || !pengarang || !penerbit || !tahun || !kategori || isNaN(stok)) {
                alert('Harap isi semua field yang wajib!');
                return;
            }
            
            // Cek apakah ada file gambar yang diunggah
            const fileUpload = document.getElementById('fileUpload');
            let sampul = null;
            
            if (fileUpload.files.length > 0) {
                const file = fileUpload.files[0];
                const reader = new FileReader();
                reader.onload = function(e) {
                    sampul = e.target.result;
                    saveNewBook(sampul);
                };
                reader.readAsDataURL(file);
            } else {
                saveNewBook(sampul);
            }
            
            function saveNewBook(sampul) {
                // Buat ID unik
                const newId = bukuData.length > 0 ? Math.max(...bukuData.map(b => b.id)) + 1 : 1;
                
                // Tambahkan buku baru
                const newBuku = {
                    id: newId,
                    judul,
                    pengarang,
                    penerbit,
                    tahun,
                    kategori,
                    stok,
                    deskripsi,
                    sampul,
                    stokHistory: [{
                        tanggal: new Date().toISOString(),
                        aksi: 'tambah',
                        jumlah: stok,
                        stokAwal: 0,
                        stokAkhir: stok,
                        catatan: 'Stok awal'
                    }]
                };
                
                bukuData.push(newBuku);
                renderBukuTable();
                
                // Reset form
                document.getElementById('formStokBuku').reset();
                document.getElementById('coverPreview').innerHTML = '<div class="cover-preview-placeholder"><i class="fas fa-book"></i></div>';
                document.getElementById('fileUpload').value = '';
                
                // Tampilkan tab data
                openTab('dataTab');
                
                alert('Buku berhasil ditambahkan!');
            }
        }
        
        // Fungsi untuk membuka tab
        function openTab(tabName) {
            // Sembunyikan semua tab content
            const tabContents = document.getElementsByClassName('tab-content');
            for (let i = 0; i < tabContents.length; i++) {
                tabContents[i].classList.remove('active');
            }
            
            // Hilangkan active class dari semua tab
            const tabs = document.getElementsByClassName('tab');
            for (let i = 0; i < tabs.length; i++) {
                tabs[i].classList.remove('active');
            }
            
            // Tampilkan tab yang dipilih
            document.getElementById(tabName).classList.add('active');
            
            // Set tab yang aktif
            event.currentTarget.classList.add('active');
            
            // Jika tab data yang dibuka, render tabel
            if (tabName === 'dataTab') {
                renderBukuTable();
            }
        }
        
        // Event listeners
        document.getElementById('formStokBuku').addEventListener('submit', tambahBuku);
        document.getElementById('editBukuForm').addEventListener('submit', simpanEditBuku);
        document.getElementById('stokForm').addEventListener('submit', simpanPerubahanStok);
        document.getElementById('cancelEdit').addEventListener('click', closeModal);
        document.getElementById('cancelStok').addEventListener('click', closeModal);
        document.querySelectorAll('.close-modal').forEach(btn => {
            btn.addEventListener('click', closeModal);
        });
        
        // Event listener untuk upload gambar sampul
        document.getElementById('fileUpload').addEventListener('change', function() {
            if (this.files.length > 0) {
                displayCoverPreview(this.files[0], 'coverPreview');
            }
        });
        
        // Event listener untuk upload gambar sampul di modal edit
        document.getElementById('editFileUpload').addEventListener('change', function() {
            if (this.files.length > 0) {
                displayCoverPreview(this.files[0], 'editCoverPreview');
            }
        });
        
        // Event listener untuk reset form
        document.getElementById('resetFormBtn').addEventListener('click', function() {
            document.getElementById('coverPreview').innerHTML = '<div class="cover-preview-placeholder"><i class="fas fa-book"></i></div>';
            document.getElementById('fileUpload').value = '';
        });
        
        // Tutup modal ketika klik di luar modal
        window.addEventListener('click', function(event) {
            if (event.target.classList.contains('modal')) {
                closeModal();
            }
        });
        
        // Pencarian buku
        document.getElementById('searchInput').addEventListener('input', function() {
            const keyword = this.value.toLowerCase();
            const hasilPencarian = bukuData.filter(buku => 
                buku.judul.toLowerCase().includes(keyword) || 
                buku.pengarang.toLowerCase().includes(keyword) ||
                buku.penerbit.toLowerCase().includes(keyword) ||
                buku.kategori.toLowerCase().includes(keyword)
            );
            renderBukuTable(hasilPencarian);
        });
        
        // Render tabel saat pertama kali load
        renderBukuTable();
    </script>
</body>
</html>
