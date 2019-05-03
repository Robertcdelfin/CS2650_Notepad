#include "mainwindow.h"
#include "ui_mainwindow.h"

MainWindow::MainWindow(QWidget *parent) :
    QMainWindow(parent),
    ui(new Ui::MainWindow)
{
    ui->setupUi(this);
    this->setCentralWidget(ui->textEdit);
}

MainWindow::~MainWindow()
{
    delete ui;
}
//Whenever sombdy clisk on a new icon do what is inside
void MainWindow::on_actionNew_triggered()
{
    //Clear the screen
    currentFile.clear();
    //Create a new text window
    ui->textEdit->setText(QString());
}

void MainWindow::on_actionOpen_triggered()
{
    QString fileName = QFileDialog::getOpenFileName(this, "OPen the File");
    QFile file(fileName);
    currentFile = fileName;
    //makes sure the file is readonlly and it is a text
    if(!file.open(QIODevice::ReadOnly | QFile::Text))
    {
        QMessageBox::warning(this, "Warning", "Can NOT open file:" + file.errorString());

    }
    //if it goes through sets the new name
    setWindowTitle(fileName);
    QTextStream in(&file); //to save the file
    QString text = in.readAll(); //read all input
    ui->textEdit->setText(text); //output everything from the input stream
    file.close();
}

void MainWindow::on_actionSave_triggered()
{
    //Open window to save a file
    QString fileName = QFileDialog::getSaveFileName(this, "Save the File");
    //Create object to hold the file
    QFile file(fileName);
    //Open the file and check if it exist
    if(!file.open(QFile::WriteOnly | QFile::Text))
    {
        QMessageBox::warning(this, "Warning", "Can NOT save file:" + file.errorString());
    }
    //store current file
    currentFile = fileName;
    //set window title to name
    setWindowTitle(fileName);
    //When writing to out we are actually writing to file on "out << text"
    QTextStream out(&file);
    //Copy text in textEdit widget
    QString text = ui->textEdit->toPlainText();

    //write to file
    out <<text;
    file.close();

}

void MainWindow::on_actionExit_triggered()
{
    QApplication::quit();
}

void MainWindow::on_actionCopy_triggered()
{
    //when you want to copy what is in the textEdit
    ui->textEdit->copy();
}

void MainWindow::on_actionPaste_triggered()
{
    ui->textEdit->paste();
}

void MainWindow::on_actionUndo_triggered()
{
    ui->textEdit->undo();
}

void MainWindow::on_actionRedo_triggered()
{
    ui->textEdit->redo();
}
