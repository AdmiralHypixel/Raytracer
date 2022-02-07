# cpp-template

When cloning this repository, please ensure you run `git submodule update --recursive` to fetch any submodule dependencies.

## Using Clang-Format
Consult the [Clang-Format Style Options documentation](https://clang.llvm.org/docs/ClangFormatStyleOptions.html) for additional configuration and formatting options.

### Visual Studio
Visual studio inclues a version of clang-format.exe that is outdated. To update and fix your clang formater, install the latest version of llvm/clang
[LLVM windows installer](https://github.com/llvm/llvm-project/releases/download/llvmorg-13.0.0/LLVM-13.0.0-win64.exe)
After installing LLVM, go to `Tools > Options > Text Editor > C/C++ > Formatting` and select `Use custom clang-format.exe file`. Click the `browse...` link then browse to `C:\Program Files\LLVM\bin\clang-format.exe`. 

From the top menu in visual studio, `Edit > Advanced > Format Document` you will notice a default keybind, you can run this at any time for format/lint your document. This can be rebound in `Tools > Options > Environment > Keyboard` The command to search for is `Edit.FormatDocument`, key combo is at the bottom.

This should be enabled by default, but if it is not:
Select the "Run ClangFormat for all formatting scenarios" option under the `Tools > Options > Text Editor > C/C++ > Formatting`. [Learn about additional configuration options.](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/#tools-options-configuration)

If you would like for files to format every time you save, [here is a extension](https://marketplace.visualstudio.com/items?itemName=mynkow.FormatdocumentonSave) to do so.

### Visual Studio _Code_
You must install the C/C++ extension. Once installed, Visual Studio Code should automatically respect the `.clang-format` file. [You may wish to enable formatting on save.](https://code.visualstudio.com/docs/cpp/cpp-ide#_code-formatting)

### CLion
CLion will automatically detect and respect the `.clang-format` file. If not, you may need to select "Enable ClangFormat" under the "Preferences > Editor > Code Style" menu. [Learn more.](https://www.jetbrains.com/help/clion/clangformat-as-alternative-formatter.html#clion-support)

## Pre-commit Formatting Hook
A pre-commit hook is included that will automatically apply the `.clang-format` rules to all modified source code files. **This pre-commit hook is a bash script and requires you have clang-format installed.**

For Windows users without a bash-like environment, we recommend using either [WSL](https://docs.microsoft.com/en-us/windows/wsl/install) or ignoring the pre-commit hook and enabling a "auto format on save" option in your IDE.

### Installing clang-format-hooks
1. [Install `clang-format` using your preferred package manager](https://github.com/barisione/clang-format-hooks#dependencies). Your IDE likely bundled a copy internally, you may wish to reconfigure it to use non-bundled installation to avoid version mismatches.
1. Double-check that you have initialized all git submodule dependencies using `git submodule update --recursive`
1. Navigate into the `clang-format-hooks/` subdirectory
1. Install the pre-commit hook using `./git-pre-commit-format install`
1. **If you prefer to use a Git GUI**, you will need to disable the pre-commit hook's interactive prompt using `git config hooks.clangFormatDiffInteractive false` ([additional documentation](https://github.com/barisione/clang-format-hooks#using-the-pre-commit-hook))

An additional `clang-format-hooks/apply-format` script is available to manually apply formatting to code changes.
