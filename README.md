import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Card, CardContent } from "@/components/ui/card";
import { UploadCloud, Twitter } from "lucide-react";

export default function CreateToken() {
  const [tokenName, setTokenName] = useState("");
  const [tokenSymbol, setTokenSymbol] = useState("");
  const [description, setDescription] = useState("");
  const [logo, setLogo] = useState(null);

  const handleLogoUpload = (event) => {
    setLogo(URL.createObjectURL(event.target.files[0]));
  };

  return (
    <div className="min-h-screen bg-gray-900 text-white flex flex-col items-center p-6">
      <h1 className="text-3xl font-bold mb-6">Create Your Token</h1>
      <Card className="w-full max-w-md bg-gray-800 p-6 rounded-2xl shadow-lg">
        <CardContent className="space-y-4">
          <div>
            <label className="block text-sm font-medium mb-1">Token Name *</label>
            <Input
              value={tokenName}
              onChange={(e) => setTokenName(e.target.value)}
              placeholder="Enter token name"
            />
          </div>
          <div>
            <label className="block text-sm font-medium mb-1">Token Symbol *</label>
            <Input
              value={tokenSymbol}
              onChange={(e) => setTokenSymbol(e.target.value)}
              placeholder="Enter token symbol"
            />
          </div>
          <div className="flex flex-col items-center border-2 border-dashed border-gray-600 p-4 rounded-xl cursor-pointer">
            <input type="file" className="hidden" onChange={handleLogoUpload} />
            {logo ? (
              <img src={logo} alt="Token Logo" className="w-20 h-20 object-cover" />
            ) : (
              <UploadCloud className="w-10 h-10 text-gray-400" />
            )}
            <p className="text-sm text-gray-400">Click to upload logo</p>
          </div>
          <div>
            <label className="block text-sm font-medium mb-1">Description *</label>
            <Textarea
              value={description}
              onChange={(e) => setDescription(e.target.value)}
              placeholder="Describe your token"
            />
          </div>
          <Button className="w-full bg-blue-600 hover:bg-blue-500">Create Token</Button>
          <a
            href="https://twitter.com/yourhandle"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center justify-center text-blue-400 hover:text-blue-300 mt-2"
          >
            <Twitter className="w-5 h-5 mr-2" /> 
          </a>
        </CardContent>
      </Card>
    </div>
  );
}
