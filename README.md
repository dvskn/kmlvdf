#include<stdio.h>
#include<stdlib.h>
#include<windows.h>
#pragma comment(lib, "WINMM.LIB")
#include<string.h>
#include<time.h>
int main()
{
	void recursur();
	int i = 0, caf = 33;
	FILE *fp ;
	clock_t stime = 0, ftime = 0;
	char buf[1920], seat[]="字符图\\ASCII-fzw (0).txt", ai[5];
	printf("Press Enter to play.\n");
	getchar();
	system("cls");

	stime = clock();
	while(i <= 349)
	{
		if(i % 30 == 0)
		{
			caf = 43;
		}
		else
		{
			caf = 33;
		}
		strcpy(seat, "字符图\\ASCII-fzw (");
		sprintf(ai, "%d", i);
		strcat(seat, ai);
		strcat(seat, ").txt");
		ftime = clock();
		if((ftime - stime) >= caf)
		{
			i++;
			fp = fopen(seat, "r");
			fread(buf, sizeof(buf), 1, fp);
			buf[1920] = '\0';
			fclose(fp);
			fprintf(stdout, "%s", buf);
			fprintf(stdout, "Frame:%d", i);
			stime += caf;
			recursur();
		}
	}
	system("cls");
	printf("Thanks for watching!\n\n\n");
	printf("Press Enter to Exit.\n");
	getchar();
	return 0;
}
void recursur()
{
	HANDLE hout;
	COORD coord;
	coord.X = 0;
	coord.Y = 0;
	hout = GetStdHandle(STD_OUTPUT_HANDLE);
	SetConsoleCursorPosition(hout,coord);
}
