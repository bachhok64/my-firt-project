#include<iostream>
#include<conio.h>
const float DiemChuan = 8;
using namespace std;
struct SinhVien
{
	char Ten[30];
	float Diem;
};
void Nhap(SinhVien* SV, int n) {
	cout << "\nNhap thong tin sinh vien:";
	for (int i = 0; i < n; i++)
	{
		cout << "\n - Ho ten sinh vien " << i + 1 << ": ";
		getchar();
		gets_s(SV[i].Ten);
		cout << " - Diem thi: ";
		cin >> SV[i].Diem;
	}
}
void HoanVi(SinhVien& a, SinhVien& b) {
	SinhVien x = a;
	a = b;
	b = x;
}
void SapXep(SinhVien* SV, int N) {
	for (int i = 0; i < N-1; i++)
	{
		for (int j = i+1; j < N; j++)
		{
			if (SV[i].Diem<SV[j].Diem)
			{
				HoanVi(SV[i], SV[j]);
			}
		}
	}
}
void Xuat(SinhVien* SV, int N,float DiemChuan) {
	if (SV[0].Diem<DiemChuan)
	{
		cout << "\nKhong co sv trung tuyen";
	}
	else
	{
		cout << "\nDS sv trung tuyen:";
		for (int i = 0; i < N; i++)
		{
			if (SV[i].Diem >= DiemChuan)
			{
				cout << "\n - " << SV[i].Ten << ": " << SV[i].Diem << " diem";
			}
		}
	}
}
int main() {
	SinhVien SV[100];
	int N;
	cout << "Nhap so luong sv: ";
	cin >> N;
	Nhap(SV, N);
	SapXep(SV, N);
	Xuat(SV, N, DiemChuan);
	return 0;
}
